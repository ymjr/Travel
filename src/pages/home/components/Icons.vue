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
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination'
      },
      iconList: [{
        id: '0001',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
        desc: '景点门票'
      }, {
        id: '0002',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/8246f27355943202.png',
        desc: '游乐场'
      }, {
        id: '0003',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png',
        desc: '亲子游'
      }, {
        id: '0004',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
        desc: '长沙必游'
      }, {
        id: '0005',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
        desc: '一日游'
      }, {
        id: '0006',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
        desc: '动植物园'
      }, {
        id: '0007',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/47/c2b659e048b11602.png',
        desc: '主题乐园'
      }, {
        id: '0008',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/b8/c5dcdb58deec2402.png',
        desc: '湘西凤凰'
      }, {
        id: '0009',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/ab/6f7d6e44963c9302.png',
        desc: '泡温泉'
      }]
    }
  },
  computed: {
    pageList () {
      function chunk (arr, size) {
        var arr2 = [ ];
        for (var i = 0; i < arr.length ; i = i + size) {
          arr2.push(arr.slice(i ,i + size)) ;
        }
        return arr2 ;
      }
      const arrayList = chunk( this.iconList , 8)
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
