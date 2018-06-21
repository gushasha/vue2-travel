<template>
<div>
  <div class="high-border-middle">
    <div class="title-group">
      <span class="title">猜你喜欢</span>
    </div>
    <ul>
      <router-link
        tag="li"
        class="item border-bottom"
        v-for="item of recommendList"
        :key="item.id"
        :to="'/detail/' + item.id"
      >
        <img class="item-image" :src="item.imgUrl" />
        <div class="item-info">
          <p class="item-title">{{ item.title }}</p>
          <p class="item-desc"> {{ item.desc }}</p>
          <button class="item-button">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    recommendList: Array
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
  overflow hidden
  display flex
  height 2rem
  padding .1rem 0
}
  .item-image {
    width 1.8rem
    height 1.8rem
    margin .1rem .25rem
  }
  .item-info {
    flex 1 // TODO: flex
    min-width 0 // TODO: min-width
  }
    .item-title {
      margin-top .2rem
      line-height .54rem
      font-size: .32rem;
      ellipse()
    }
    .item-desc {
      line-height .5rem
      color #cccccc;
      ellipse()
    }
    .item-button {
      background orange
      color #ffffff
      margin-top .1rem
      padding .05rem
      font-size .25rem
      border-radius .1rem
    }
</style>
