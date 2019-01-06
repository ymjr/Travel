<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom" v-for="list of recommendList" :key="list.id">
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
  data () {
    return {
      recommendList: [{
        id: '001',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1505/fb/302620ed8350f8.jpg_r_640x214_25a07cb4.jpg',
        title: '长沙必打卡',
        desc: '到了长沙，一定要到这些地方走走'
      }, {
        id: '002',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1711/2b/d4ebbd8337f1ac.jpg_r_640x214_2d4332c1.jpg',
        title: '湖南泡汤圣地',
        desc: '山谷幽深，泉水潺潺，宜人的自然风光，怡人的田园景色，动人的神话传说，是一处难得的世外桃园'
      }, {
        id: '003',
        imgUrl: 'http://img1.qunarzz.com/sight/source/1811/88/8d3b492ebf0b16.jpg_r_640x214_7b3a281d.jpg',
        title: '邂逅凤凰城',
        desc: '凤凰古城一个古老而神秘的地方，风景秀丽，历史悠久，人杰地灵，名贤辈出，名胜古迹众多'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~&styles/mixins.styl"
  .title
    line-height :.4rem
    background :#eee
    text-indent :.2rem
    margin-top :.2rem
    margin-bottom :.2rem
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
