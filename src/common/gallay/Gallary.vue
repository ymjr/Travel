<template>
  <div class="container" @click="handleClick">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide v-for="(item ,index) in gallaryImgs" :key="index">
          <img class="gallary-img" :src="item"/>
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props: {
    gallaryImgs: {
      type: Array
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observer: true,
        observeParents: true
      }
    }
  },
  methods: {
    handleClick () {
      this.$emit('change')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow :inherit
  .container
    display :flex
    flex-direction :column
    justify-content :center
    z-index :99
    position: fixed
    left :0
    right :0
    top:0
    bottom :0
    background :#000
    .wrapper
      width :100%
      height :0
      padding-bottom :99%
      background :#ffffff
    .gallary-img
      width :100%
    .swiper-pagination
      color:#ffffff
      bottom :-.4rem

</style>
