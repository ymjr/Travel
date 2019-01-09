<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list :hotCities="hotCities" :cities="cities" :letter="letter"></city-list>
    <city-alphabe :cities="cities" @change="handleLetterChange"></city-alphabe>
  </div>
</template>

<script>
import CityHeader from './components/header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabe from './components/Alphabet'
import axios from 'axios'

export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabe
  },
  data () {
    return {
      hotCities: [ ],
      cities: {},
      letter: ''
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/city.json')
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        this.hotCities = res.data.hotCities
        this.cities = res.data.cities
      }
    },
    handleLetterChange (stp) {
      this.letter = stp
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style scoped>

</style>
