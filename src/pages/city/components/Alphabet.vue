<template>
  <ul class="list" ref="list">
    <li
      class="item"
      v-for="item of letters"
      :key="item"
      :ref="item"
      @click="handleLetterClick"
      @touchstart = "handleTouchStart"
      @touchmove = "handleTouchMove"
      @touchend = "handleTouchend"
    >{{item}}</li>
  </ul>
</template>

<script>
export default {
  name: 'Alphabet',
  props: {
    cities: Object
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      startH: 0,
      startUl: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
    this.startH = this.$refs['A'][0].offsetHeight
    this.startUl = this.$refs.list.offsetTop
  },
  methods: {
    handleLetterClick (event) {
      this.$emit('change', event.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - this.startUl
          const index = Math.floor((touchY - this.startY) / this.startH)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchend () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~&styles/varibles.styl"
  .list
    position:absolute
    top:1.58rem
    right:0
    bottom :0
    display:flex
    flex-direction :column
    justify-content :center
    width :.4rem
    text-align :center
    .item
      line-height :.4rem
      color:$bgColor
</style>
