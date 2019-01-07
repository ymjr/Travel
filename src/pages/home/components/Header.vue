<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{city}}
        <span class="iconfont arrow-icon">&#xe64a;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  props: {
    city: String
  },
  name: 'HomeHeader'
}
</script>

<style lang="stylus" scoped>
  @import "~&styles/varibles.styl"
  .header
    display: flex
    line-height: $headerHeight
    background-color: $bgColor
    color: #fff
    height :$headerHeight
    .header-left
      width: .64rem
      float: left
      .back-icon
        text-align: center
        font-size: .4rem
    .header-input
      flex: 1
      height: .64rem
      line-height: .64rem
      margin-top: .12rem
      margin-left: .2rem
      background: #fff
      border-radius: .06rem
      color: #ccc
      padding-left: .2rem
    .header-right
      width: 1.24rem
      float: right
      text-align: center
      color:#ffffff
      .arrow-icon
        font-size: .24rem
        margin-left: -.04rem
</style>
