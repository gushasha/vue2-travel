<template>
  <div>
    <div class="header">
      <div class="header-left">
        <div class="iconfont back-icon">&#xe624;</div>
      </div>
      <div class="header-input">
        <span class="icon iconfont">&#xe632;</span>
        <span>输入城市/景点/游玩主题</span>
      </div>
      <div class="header-right">
        <router-link to="/city" class="router-style">
          <span>{{ city }}</span>
          <span class="iconfont arrow-icon">&#xe64a;</span>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import {mapState} from 'vuex'

export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  },
  data () {
    return {}
  }
}
</script>

<style lang="stylus" scoped>

  @import '~styles/veribles.styl';
  .header {
    height: $headerHeight;
    line-height: $headerHeight;
    display: flex;
    background-color: $bgColor;
    color: #FFF;
  }

  .header-left {
    float: left;
    width: .7rem;
  }
    .back-icon {
      font-size: .38rem
      text-align: center
    }
  .header-input {
    flex: 1;
    background-color: #FFF;
    border-radius: .08rem;
    margin-top: .12rem;
    margin-left: .12rem;
    height: .64rem;
    line-height: .64rem;
    color: #ccc;
    padding-left: .4rem;
  }

  .header-right {
    float: right;
    min-width: 1.24rem;
    padding: 0 .2rem;
    text-align: center;
  }
    .router-style {
      color: #ffffff;
    }
  .arrow-icon {
    margin-left: -.05rem;
    font-size: .24rem;
  }
</style>
