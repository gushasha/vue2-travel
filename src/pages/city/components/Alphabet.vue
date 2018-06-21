<template>
  <!-- touchstart.prevent 阻止默认行为 -->
  <ul class="list">
    <li
        class="item"
        :ref="item"
        v-for="item of letters"
        :key="item"
        @click="handleClick"
        @touchstart.prevent="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
    >
      {{ item }}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    // 计算字母A到顶部的高度
    this.startY = this.$refs['A'][0].offsetTop
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  methods: {
    handleClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (!this.touchStatus) {
        return
      }
      // x
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        // 计算字母A到顶部的高度

        // 手指到顶部的高度
        const touchY = e.touches[0].clientY
        // 手指对应的字母
        const index = Math.floor((touchY - this.startY) / 20)
        if (index >= 0 && index < this.letters.length) {
          this.$emit('change', this.letters[index])
        }
      }, 16)
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style scoped lang="stylus">
@import "~styles/veribles.styl";

.list {
  position: absolute;
  top:1.58rem;
  right:0;
  bottom:0;
  width: .8rem;
  display: flex;
  flex-direction:column;
  justify-content: center;
}
  .item {
    color: $bgColor;
    height: .4rem;
    line-height: .4rem;
    text-align: center;
  }
</style>
