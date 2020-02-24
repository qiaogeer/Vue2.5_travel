<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img
        :src="bannerImg"
        class="banner-img"
      />
      <div class="banner-info">
        <div class="banner-title">{{sightName}}</div>
        <div class="banner-number">
          <i class="banner-icon iconfont">&#xe606;</i>39
        </div>
      </div>
    </div>
    <common-gallary :imgs='gallaryImgs' v-show="showGallary" @close='handleGallaryClose'></common-gallary>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name: 'DetailBanner',
  components: {
    CommonGallary
  },
  data() {
    return {
      showGallary: false
    }
  },
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  methods: {
    handleBannerClick() {
      this.showGallary = !this.showGallary
    },
    handleGallaryClose() {
      this.showGallary = !this.showGallary
    }
  }
}
</script>

<style lang='stylus' scoped>
.banner {
  position: relative;
  overflow: hidden;
  height: 0;
  padding-bottom: 55%;

  .banner-img {
    width: 100%;
  }

  .banner-info {
    display: flex;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    line-height: 0.6rem;
    color: #fff;
    background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));

    .banner-title {
      flex: 1;
      font: size 0.32rem;
      padding: 0 0.2rem;
    }

    .banner-number {
      height: 0.32rem;
      line-height: 0.32rem;
      margin-top: 0.14rem;
      padding: 0 0.4rem;
      border-radius: 0.2rem;
      background: rgba(0, 0, 0, 0.8);
      font-size: 0.24rem;

      .banner-icon {
        font-size: 0.24rem;
      }
    }
  }
}
</style>
