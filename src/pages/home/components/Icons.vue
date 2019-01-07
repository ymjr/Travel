<template>
  <div class="icons">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide v-for="(page,index) in pageList" :key="index">
          <div class="icon" v-for="item in page" :key="item.id">
            <div class="icon-img">
              <img class="icon-img-content" :src="item.imgUrl"/>
            </div>
            <p class="icon-desc">{{item.desc}}</p>
          </div>
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    iconList: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    pageList () {
      function chunk (arr, size) {
        var arr2 = []
        for (var i = 0; i < arr.length; i = i + size) {
          arr2.push(arr.slice(i, i + size))
        }
        return arr2
      }
      const arrayList = chunk(this.iconList, 8)
      return arrayList
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~&styles/mixins.styl"
  .icons >>> .swiper-container
    width :100%
    overflow :hidden
    height :0
    padding-bottom :54%
  .icons >>>.swiper-container-horizontal > .swiper-pagination-bullets
    bottom: -2px;
    left: 0;
    width: 100%;
  .icons
    margin-top :.1rem
    .icon
      position:relative
      float:left
      width :25%
      height :0
      padding-bottom :25%
      .icon-img
        position: absolute
        top :0
        left :0
        right :0
        bottom : .44rem
        overflow :hidden
        text-align :center
        box-sizing :border-box
        padding-top :.2rem
        .icon-img-content
          height :100%
      .icon-desc
        position:absolute
        left :0
        right :0
        bottom :0
        line-height :.44rem
        text-align :center
        ellipsis()
</style>
