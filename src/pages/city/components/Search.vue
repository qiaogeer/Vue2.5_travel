<template>
  <div>
    <div class="search">
      <input type="text" placeholder="输入城市名或者拼音" class="search-input" v-model="keyword" />
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li v-for="item in list" :key="item.id" class="search-item border-bottom" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom" v-show = "hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import {mapMutations} from 'vuex'
export default {
  name: "CitySearch",
  data() {
    return {
      keyword: "",
      list: [],
      timer: null
    };
  },
  computed:{
    hasNoData(){
      return !this.list.length
    }
  },
  methods: {
      handleCityClick(city) {
      this.changeCity(city)
      this.$router.push('/')
    },
     ...mapMutations(['changeCity']),
  },
  watch : {
    keyword() {
      if (this.timer) {
        clearTimeout(this.timer);
      }
      if(!this.keyword){
        this.list=[]
        return
      }
      this.timer = setTimeout(() => {
        const result = [];
        for (let i in this.cities) {
          this.cities[i].forEach(value => {
            if (
              value.spell.indexOf(this.keyword) > -1 ||
              value.name.indexOf(this.keyword) > -1
            ) {
              result.push(value);
            }
          });
        }
        this.list = result;
      }, 100);
    }
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.search) 
  },
  props: {
    cities: Object
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.search {
  text-align: center;
  background: $bgColor;
  padding: 0.1rem;
  heigh: 0.72rem;
}

.search-input {
  height: 0.62rem;
  line-height: 0.62rem;
  width: 100%;
  border-radius: 0.06rem;
  text-align: center;
  padding: 0.1rem;
  box-sizing: border-box;
}

.search-content {
  overflow: hidden;
  position: absolute;
  top: 1.68rem;
  left: 0;
  right: 0;
  bottom: 0;
  background: #eee;
  z-index: 1;

  .search-item {
    line-height: 0.62rem;
    padding-left 0.2rem;
    color: #666;
    background:#fff
  }
}
</style>
