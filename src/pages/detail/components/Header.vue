<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <div class="iconfont header-abs-back">&#xe624;</div>
    </router-link>
    <transition>
      <div class="header-fixed" v-show="!showAbs">
        景点详情
        <router-link to="/">
          <div class="iconfont header-fixed-back">&#xe624;</div>
        </router-link>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      showAbs: true
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~&styles/varibles.styl'
  .v-enter,.v-leave-to
    opacity: 0;
  .v-enter-active,.v-leave-active
    transition: opacity 0.8s;
  .header-abs
    position :absolute
    left:.2rem
    top:.2rem
    width :.76rem
    height :.76rem
    line-height :.76rem
    border-radius :.4rem
    text-align :center
    background :rgba(0,0,0,.4)
    .header-abs-back
      color:#ffffff
      font-size :.4rem
  .header-fixed
    z-index :2
    position:fixed
    top :0
    left :0
    right :0
    overflow :hidden
    height:$headerHeight
    line-height :$headerHeight
    text-align :center
    color:#fff
    background :$bgColor
    font-size :.32rem
    .header-fixed-back
      color:#fff
      position:absolute
      top:0
      left:0
      width :.64rem
      text-align :center
      font-size :.4rem

</style>
