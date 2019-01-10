<template>
  <div>
    <banner-default :gallaryImgs="gallaryImgs" :title="title" :bannerImg="bannerImg"></banner-default>
    <header-default></header-default>
    <detail-list :list="list"></detail-list>
    <div class="contianer"></div>
  </div>
</template>

<script>
import BannerDefault from './components/Banner'
import HeaderDefault from './components/Header'
import DetailList from './components/List'
import axios from 'axios'

export default {
  name: 'Detail',
  components: {
    BannerDefault,
    HeaderDefault,
    DetailList
  },
  data () {
    return {
      list: [ ],
      bannerImg: '',
      gallaryImgs: [],
      title: '',
      lastId: ''
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/detail.json?id=' + this.$route.params.id)
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        this.bannerImg = res.data.bannerImg
        this.list = res.data.categoryList
        this.gallaryImgs = res.data.gallaryImgs
        this.title = res.data.sightName
      }
    }
  },
  mounted () {
    this.lastId = this.$route.params.id
    this.getHomeInfo()
  },
  activated () {
    if (this.lastId != this.$route.params.id) {
      this.lastId = this.$route.params.id
      this.getHomeInfo()
    }
  }
}
</script>

<style lang="stylus" scoped>
  .contianer
    height :66rem
</style>
