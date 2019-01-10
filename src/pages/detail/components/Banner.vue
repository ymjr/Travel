<template>
  <div>
    <div class="banner" @click="handleClick">
      <img class="banner-img" :src="bannerImg"/>
      <div class="banner-info">
        <div class="banner-icon"><span class="iconfont bannerIcon">&#xe796;</span><em class="banner-icon-number">{{gallaryImgs.length}}</em></div>
        <div class="banner-tittle">{{title}}</div>
      </div>
    </div>
    <fade-animation>
      <common-gallary :gallaryImgs="gallaryImgs" v-show="show"  @change="handleChange"></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import CommonGallary from '&common/gallay/Gallary'
import FadeAnimation from '&common/fade/FadeAnimation'

export default {
  name: 'DetailBanner',
  components: {
    CommonGallary,
    FadeAnimation
  },
  props: {
    gallaryImgs: Array,
    title: String,
    bannerImg: String
  },
  data () {
    return {
      show: false
    }
  },
  methods: {
    handleClick () {
      this.show = true
    },
    handleChange () {
      this.show = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position :relative
    overflow :hidden
    height :0
    padding-bottom :55%
    .banner-img
      width :100%
    .banner-info
      position :absolute
      left :0
      right :0
      bottom :0
      background-image : linear-gradient(top,rgba(0,0,0,0) ,rgba(0,0,0,0.8))
      padding-left :.2rem
      .banner-icon
        width: 1.2rem;
        height: .4rem;
        background: rgba(0,0,0,.5);
        border-radius: .2rem;
        font-size: .24rem;
        color: #fff;
        line-height: .4rem;
        text-align :center
        margin-bottom :.1rem
        .bannerIcon
          margin-left :-.3rem
        .banner-icon-number
          position :absolute
          margin-left :.1rem
      .banner-tittle
        margin-bottom :.3rem
        line-height: .4rem;
        color: #fff;
        font-size: .36rem;
</style>
