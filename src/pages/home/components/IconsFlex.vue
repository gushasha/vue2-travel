<template>
  <div>
    <swiper class="icon-box">
      <swiper-slide v-for="(page, index) of pages" :key="index"  class="icons">
          <div class="icon" v-for="item of page" :key="item.id">
            <div class="icon-img">
              <img class="icon-img-content" :src="item.imgUrl"/>
            </div>
            <p class="icon-desc" v-text="item.desc"></p>
          </div>
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

.icon-box {
  background: #ffffff;
}
  .icons {
    width: 100%;
    display: flex;
    flex-flow: row wrap;
    align-content: flex-start;
    margin: .2rem 0
  }

  .icon {
    height: 0;
    width:100%;
    padding-bottom: 22%;
    box-sizing: border-box;
    flex: 0 0 25%;
    overflow:hidden;
    margin: .1rem 0
    position: relative
  }
    .icon-img-content {
      position: absolute
      top: 0
      left: 0
      right: 0
      bottom: .44rem
      width: 65%
      display: block
      margin: 0 auto
    }
    .icon-desc {
      position: absolute
      left: 0
      right: 0
      bottom: 0
      height: .44rem
      line-height: .44rem
      text-align: center
      color: $darkTextColor
      ellipse()
    }
</style>
