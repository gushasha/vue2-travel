<template>
  <div>
    <city-header></city-header>
    <city-search
        :cities="cities"
    ></city-search>
    <city-list
        :hotCities="hotCities"
        :cities="cities"
        :letter="letter"
    ></city-list>
    <city-alphabet
        :cities="cities"
        @change="changeLetter"
    ></city-alphabet>
  </div>
</template>

<script>
import CityHeader from './components/Header.vue'
import CitySearch from './components/Search.vue'
import CityList from './components/List.vue'
import CityAlphabet from './components/Alphabet.vue'
import axios from 'axios'

export default {
  name: 'City',
  data () {
    return {
      hotCities: [],
      cities: {},
      letter: ''
    }
  },
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  mounted () {
    this.getCityInfo()
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city').then((res) => {
        this.getCityInfoSuccess(res)
      })
    },
    getCityInfoSuccess (res) {
      if (res.data.ret !== true) {
        alert('error....')
        return
      }
      if (!res.data.data) {
        alert('空数据')
        return
      }
      const data = res.data.data
      this.hotCities = data.hotCities
      this.cities = data.cities
    },
    changeLetter (letter) {
      this.letter = letter
    }
  }
}
</script>

<style lang="stylus" scoped></style>
