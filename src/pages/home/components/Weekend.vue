<template>
<div>
  <div class="high-border-middle">
    <div class="title-group ">
      <span class="title">周末去哪儿</span>
    </div>
    <ul>
      <li
        class="item border-topbottom"
        v-for="item of weekendList"
        :key="item.id"
      >
        <div class="item-image-wrapper">
          <img class="item-image" :src="item.imgUrl" />
        </div>
        <div class="item-info">
          <p class="item-title">{{ item.title }}</p>
          <p class="item-desc"> {{ item.desc }}</p>
        </div>
      </li>
    </ul>
  </div>
</div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    weekendList: Array
  }
}
</script>

<style lang="stylus" scoped>
@import "~styles/mixins.styl"
.high-border-middle {
  margin-top .2rem
  background #ffffff
}
.title-group {
}
  .title {
    height 1rem
    line-height 1rem
    margin-left .2rem
    font-size .34rem
  }

.item {
  padding-top .2rem
}
  .item-image-wrapper {
    width 100%
    height 0
    padding-bottom  37.06%
  }
    .item-image {
      width 100%
    }
  .item-info {
    padding 0 .2rem
  }
    .item-title {
      margin-top .2rem
      line-height .40rem
      font-size: .30rem;
      ellipse()
    }
    .item-desc {
      line-height .5rem
      color #777;
      ellipse()
    }
</style>
