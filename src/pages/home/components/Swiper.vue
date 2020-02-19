<template>
<div class="wrapper">
<swiper :options="swiperOption" >
    <swiper-slide v-for="item in list" :key="item.id">
      <img class="swiper-img" :src="item.imgUrl"></swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</div>
</template>

<script>
export default{
  name: 'HomeSwiper',
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      } 
    }
  },
  props: {
    list:Array
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper >>>.swiper-pagination-bullet-active
    background :#fff
  .wrapper
    overflow:hidden
    width :100%
    height:0
    padding-bottom :30.47%
    .swiper-img
      width:100%
</style>
