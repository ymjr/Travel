<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom" v-for="list of weekendList" :key="list.id">
        <div class="item-img-wrapper">
          <img class="item-img" :src='list.imgUrl'/>
        </div>
        <div class="item-info">
          <p class="item-title">{{list.title}}</p>
          <p class="item-desc">{{list.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    weekendList: {
      type: Array
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~&styles/mixins.styl"
  .title
    line-height :.8rem
    background :#eee
    text-indent :.2rem
  .item-img-wrapper
    overflow : hidden
    height :0
    padding-bottom:36.64%
    .item-img
      width :100%
  .item-info
    padding: .14rem .2rem .2rem .2rem;
    .item-title
      height: .44rem;
      line-height :.44rem
      font-size :.32rem
    .item-desc
      line-height: .42rem;
      color :#ccc
      ellipsis()

</style>
