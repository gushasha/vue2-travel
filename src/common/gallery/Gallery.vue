<template>
  <div class="container" @click="handleClickGallery">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide v-for="(item, index) of imgs" :key="index">
          <img class="gallery-img" :src="item" />
        </swiper-slide>
        <!-- Optional controls -->
      </swiper>
      <div class="swiper-pagination"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallery',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination',
          type: 'fraction'
        },
        observer: true,
        observeParents: true // observer: http://www.swiper.com.cn/api/observer/218.html
      }
    }
  },
  methods: {
    handleClickGallery () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
.container >>> .swiper-wrapper {
  align-items: center;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 99;
  position: fixed;
  top:0;
  bottom: 0;
  left: 0;
  right: 0;
  background: #000;
}
  .wrapper {
    width: 100%;
  }
    .gallery-img {
      width: 100%;
    }
  .swiper-pagination {
    color: #fff;
  }
</style>
