<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="list of recommendList" :key="list.id">
          <img class="item-img" :src='list.imgUrl'/>
        <div class="item-info">
          <p class="item-title">{{list.title}}</p>
          <p class="item-desc">{{list.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    recommendList: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import "~&styles/mixins.styl"
  .recommend-title
    line-height :.4rem
    background :#eee
    text-indent :.2rem
    margin-top :.2rem
  .item
    overflow:hidden
    display :flex
    height:2rem
    padding :.2rem
    .item-img
      width :2rem
      height :2rem
    .item-info
      flex :1
      padding-left: .22rem
      min-width :0
      .item-title
        margin-top: .26rem;
        height: .44rem;
        line-height :.44rem
        font-size :.32rem
      .item-desc
        margin-top: .14rem;
        height: .34rem;
        color :#ccc
        ellipsis()
      .item-button
        margin-top :.22rem
        line-height: .44rem
        background :#ff9300
        padding : 0 .1rem
        border-radius: .06rem
        color:#fff

</style>
