<template>
  <div>
    <div class="banner" @click="handleClick">
      <img class="banner-img" src="http://img1.qunarzz.com/sight/p0/201403/10/df94368ff58ae7b12313077f6851b335.jpg_600x330_8c36bb4d.jpg"/>
      <div class="banner-info">
        <div class="banner-icon"><span class="iconfont bannerIcon">&#xe796;</span><em class="banner-icon-number">3</em></div>
        <div class="banner-tittle">大围山滑雪场</div>
      </div>
    </div>
    <common-gallary :imgs="imgs" v-show="show"  @change="handleChange"></common-gallary>
  </div>
</template>

<script>
import CommonGallary from '&common/gallay/Gallary'

export default {
  name: 'DetailBanner',
  components: {
    CommonGallary
  },
  data () {
    return {
      imgs: ['//img1.qunarzz.com/sight/p0/201403/10/df94368ff58ae7b12313077f6851b335.jpg_600x330_8c36bb4d.jpg', '//img1.qunarzz.com/sight/p0/201403/10/df94368ff58ae7b12313077f6851b335.jpg_600x330_8c36bb4d.jpg'],
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
