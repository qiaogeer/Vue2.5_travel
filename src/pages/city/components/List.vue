<template>
  <div class="list" ref="wrapper">
    <div>
    <div class="area">
      <div class="title border-topbottom">当前城市</div>
      <div class="button-list">
        <div class="button-wrapper">
          <div class="button">{{this.currentCity}}</div>
          </div>
          
      </div>
    </div>
    <div class="area">
      <div class="title border-topbottom">热门城市</div>
      <div class="button-list">
      <div class="button-wrapper" v-for="item in hot" :key="item.id">
          <div class="button" @click="handleCityClick(item.name)">{{item.name}}</div>
      </div>
      </div>
    </div>
    <div class="area" v-for="(item,key) in cities" :key="key" :ref='key'>
      <div class="title border-topbottom">{{key}}</div>
      <div class="item-list" v-for="city in item" :key='city.id'>
        <div class="item border-bottom " @click="handleCityClick(city.name)">{{city.name}}</div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import {mapState,mapMutations} from 'vuex'
export default {
  name: 'CityList',
  computed:{
    ...mapState({
      currentCity : 'city'
    })
  },
  mounted() {
    this.scroll=new Bscroll(this.$refs.wrapper)
  },
  props: {
    cities: Object,
    hot: Array,
    letter: String
  },
  methods: {
    handleCityClick(city) {
      this.changeCity(city)
      this.$router.push('/')
    },
     ...mapMutations(['changeCity']),
  },
  watch:{
    letter() {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .border-topbottom
    &:before
      border-color :#ccc
    &:after
      border-color:#ccc
  .border-bottom
  &:before
    border-color :#ccc
  .list
    overflow:hidden
    position:absolute
    top:1.68rem
    left:0
    right :0
    bottom:0
    .title
      line-height :.44rem
      background:#eee
      padding-left:.2rem
      color:#666  
      font-size:.26rem
    .button-list
      padding 0.1rem .6rem .1rem .1rem
      overflow:hidden

      .button-wrapper
        float:left
        width:33.33%
        .button
          text-align:center
          margin:.1rem
          border:.02rem solid #cccccc
          border-radius:.06rem
          padding:.1rem 0
    .item-list
      .item
        line-height :.54rem
        color:#666
        padding-left:.2rem
</style>
