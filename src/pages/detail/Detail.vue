<template>
  <div>
    <detail-banner
        :sightName="sightName"
        :bannerImg="bannerImg"
        :galleryImgs="galleryImgs"
    ></detail-banner>
    <detail-header></detail-header>
    <detail-list
        :categoryList="categoryList"
    ></detail-list>
  </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'

export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      galleryImgs: [],
      categoryList: []
    }
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.HandleGetDataSuccess)
    },
    HandleGetDataSuccess (res) {
      if (res.data.ret && res.data.data) {
        const data = res.data.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.galleryImgs = data.galleryImgs
        this.categoryList = data.categoryList
      } else {
        alert('error...')
      }
    }
  },
  mounted () {
    this.getDetailInfo()
  }
}
</script>

<style lang="stylus" scroped>
.body-height {
  height: 20rem;
}
</style>
