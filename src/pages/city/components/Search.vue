<template>
<div class="search" >
  <div><input class="search-input"
              placeholder="输入城市名称或拼音"
              v-model="keyword"
        >
  </div>
  <div
      class="search-result"
      v-show="keyword"
      ref="search"
  >
    <div>
      <div class="search-item border-bottom"
           v-for="item of list"
           :key="item.id"
           @click="handleCityClick(item.name)"
      >{{ item.name }}</div>
    </div>
    <div
        class="search-item border-bottom"
         v-show="hasNoData"
    >
      没有查到数据...
    </div>
  </div>
</div>
</template>

<script>
import Bscroll from 'better-scroll'
import {mapMutations} from 'vuex'

export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search)
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          for (let item of this.cities[i]) {
            if (item.spell.indexOf(this.keyword) > -1 || item.name.indexOf(this.keyword) > -1) {
              result.push(item)
            }
          }
        }
        this.list = result
      }, 100)
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "~styles/veribles.styl";

.search {
  background-color: $bgColor;
  height: .72rem;
  padding: 0 .1rem;
}
  .search-input {
    width:100%;
    color: #666;
    height: .6rem;
    line-height: .6rem;
    border-radius: .06rem;
    text-align: center;
    padding: 0 .1rem;
    box-sizing: border-box;
  }
.search-result {
  position: absolute;
  top:$headerHeight + .72rem;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1;
  background: #fff;
  overflow: hidden;
}
  .search-item {
    color: #777;
    height: .54rem;
    line-height: .54rem;
    padding-left: .3rem;
  }
</style>
