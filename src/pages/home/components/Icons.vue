<template>
  <div class="icons">
    <swiper>
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <router-link
            :to="'detail/'+ item.id"
            tag="div"
            class="icon"
            v-for="item of page"
            :key="item.id"
        >
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl"/>
          </div>
          <p class="icon-desc" v-text="item.desc"></p>
        </router-link>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    iconList: Array
  },
  computed: {
    pages () {
      let pages = []
      this.iconList.forEach((item, index) => {
        let page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/veribles.styl'
@import '~styles/mixins.styl'

.icons >>> .swiper-container {
  width: 100%
  height: 0
  padding-bottom: 50%
  background: #ffffff;
}
.icon {
  float:left
  width: 25%
  height: 0
  padding-bottom: 25%
  position: relative
}
.icon-img {
  position: absolute
  top: .1rem
  left: 0
  right: 0
  bottom: .44rem
  box-sizing: boder-box
  padding: .1rem
}
.icon-img-content {
  width: 60%
  display: block
  margin: 0 auto
}
.icon-desc {
  position: absolute
  left: 0
  right: 0
  bottom: .1rem
  height: .44rem
  line-height: .44rem
  text-align: center
  color: $darkTextColor
  ellipse()
}
</style>
