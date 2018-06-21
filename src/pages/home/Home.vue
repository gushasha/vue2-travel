<template>
    <div class="background-style">
      <home-header></home-header>
      <home-swiper :swiperList="swiperList"></home-swiper>
      <home-icons :iconList="iconList"></home-icons>
      <home-recommend :recommendList="recommendList"></home-recommend>
      <home-weekend :weekendList="weekendList"></home-weekend>
    </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import {mapState} from 'vuex'

export default{
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  data () {
    return {
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index?city=' + this.city).then((res) => {
        this.getHomeInfoSuccess(res)
      })
    },
    getHomeInfoSuccess (res) {
      if (res.data.ret !== true) {
        alert('error....')
        return
      }
      if (!res.data.data) {
        alert('空数据')
        return
      }
      const data = res.data.data
      this.swiperList = data.swiperList
      this.iconList = data.iconList
      this.recommendList = data.recommendList
      this.weekendList = data.weekendList
    }
  },
  mounted () {
    this.getHomeInfo()
  },
  activated () {
    this.getHomeInfo()
  },
  deactivated () {}
}
</script>

<style scoped>
.background-style {
  background: #eeeeee;
}
</style>
