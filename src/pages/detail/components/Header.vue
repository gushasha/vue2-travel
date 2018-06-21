<template>
  <div>
    <div class="header-abs" v-show="showAbs">
      <router-link
          tag="div"
          class="iconfont back-icon"
          to="/"
      >
        <span class="header-abs-info">&#xe624;</span>
      </router-link>
    </div>
    <div
        class="header-fixed"
        v-show="!showAbs"
        :style="opacityStyle"
    >
      <router-link to="/">
        <span class="iconfont header-fixed-back-icon">&#xe624;</span>
      </router-link>
      <span class="">景点详情</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      /* 绑定动态style实现拖动渐隐渐现效果 */
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      /* 获取scrollTop值，解决浏览器兼容问题 */
      const scrollTop = document.body.scrollTop || document.documentElement.scrollTop
      if (scrollTop > 60) {
        let opacity = scrollTop / 140
        /* 根据拖动高度，计算opacity值 */
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = { opacity }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    /* 特别注意：在window上绑定全局事件，必须要解绑，否则在任何一个组件/页面都继续生效 */
    window.addEventListener('scroll', this.handleScroll) // 监听滚动事件
  },
  deactivated () {
    /* 特别注意：解绑全局事件 */
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import "~styles/veribles.styl"

.header-abs {
  position: fixed;
  top: .2rem;
  left: .2rem;
  width: .8rem;
  height: .8rem;
  border-radius: .4rem;
  line-height: .8rem;
  text-align: center;
  background: rgba(0, 0, 0, .5);
}
  .header-abs-info {
    color: #fff;
    font-size:.4rem;
  }

.header-fixed {
  position: fixed;
  top:0;
  left: 0;
  right: 0;
  width: 100%;
  height: $headerHeight;
  line-height: $headerHeight;
  background: $bgColor;
  color: #ffffff;
  font-size:.36rem;
  text-align: center;
  overflow: hidden;
}
.header-fixed-back-icon {
  position: absolute;
  top: 0;
  left: .4rem;
  color: #ffffff;
  font-size:.4rem;
}
</style>
