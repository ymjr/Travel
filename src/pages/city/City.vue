<template>
  <div>
    <city-header></city-header>
    <city-search></city-search>
    <city-list :City="City" :hotCities="hotCities" :cities="cities"></city-list>
    <city-alphabe :cities="cities"></city-alphabe>
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
      City: '',
      hotCities: [ ],
      cities: {}
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/city.json')
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      console.log(res)
      if (res.ret && res.data) {
        this.City = res.data.city
        this.hotCities = res.data.hotCities
        this.cities = res.data.cities
      }
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style scoped>

</style>
