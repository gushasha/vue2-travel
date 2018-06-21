<template>
  <div class="header">
    <router-link to="/">
      <span class="iconfont back-icon">&#xe624;</span>
    </router-link>
    <span class="">选择城市</span>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style scoped lang="stylus">

  @import "~styles/veribles.styl"

  .header {
    position: relative;
    width: 100%;
    height: $headerHeight;
    line-height: $headerHeight;
    background: $bgColor;
    color: #ffffff;
    font-size:.36rem;
    text-align: center;
    overflow: hidden;
  }
    .back-icon {
      position: absolute;
      top: 0;
      left: .2rem;
      color: #ffffff;
      font-size:.4rem;
    }
</style>
