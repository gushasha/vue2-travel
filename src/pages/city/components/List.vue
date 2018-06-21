<template>
  <div class="list" ref="wrapper">
    <div >
      <div class="area" >
        <div class="title border-topbottom">我的城市</div>
        <div class="button-list">
          <div class="button-wrap">
            <div class="button">{{ city }}</div>
          </div>
        </div>
      </div>
      <div class="area" >
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div
              class="button-wrap"
              v-for="item of hotCities"
              :key="item.id"
              @click="handleCityClick(item.name)"
          >
            <div class="button">{{ item.name }}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(cityGroup, key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom wrapper">{{ key }}</div>
        <div class="item-list content">
          <div
              class="item border-bottom"
              v-for="city of cityGroup"
              :key="city.id"
              @click="handleCityClick(city.name)"
          >
            {{ city.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import {mapState, mapMutations} from 'vuex'

export default {
  name: 'CityList',
  props: {
    hotCities: Array,
    cities: Object,
    letter: String
  },
  computed: {
    ...mapState(['city'])
  },
  watch: {
    letter () {
      this.scroll.scrollToElement(this.$refs[this.letter][0])
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
    this.scroll = new BScroll(this.$refs.wrapper)
  }
}

</script>

<style scoped lang="stylus">
@import "~styles/mixins.styl";
@import "~styles/veribles.styl";

.border-topbottom {
  &:before{
     border-color:#777;
   }
  &:after{
     border-color:#777;
   }
}

.list {
  position: absolute;
  top:$headerHeight + .72rem;
  left: 0;
  bottom:0;
  right:0;
  overflow: hidden;
}
.title {
  background: #eee;
  height: .65rem;
  line-height: .65rem;
  padding-left: .2rem;
}
.button-list {
  overflow: hidden;
  padding: .1rem .5rem .1rem .1rem ;
}
  .button-wrap {
    width: 33.33%;
    float: left;
  }
    .button {
      height: .5rem;
      line-height:.5rem;
      margin: .1rem;
      text-align: center;
      border:.02rem solid #ccc;
      border-radius: .08rem;
      ellipse();
    }
.item-list {
}
  .item {
    height: .64rem;
    line-height: .64rem;
    padding-left: .2rem;
  }
</style>
