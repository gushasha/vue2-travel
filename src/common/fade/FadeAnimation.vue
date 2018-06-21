<template>
  <transition>
    <slot></slot>
  </transition>
</template>

<script>
export default{
  name: 'CommonFadeAnimation'
}
</script>

<style scoped>
.v-enter, .v-leave-to {
  opacity: 0;
}
.v-enter-active, .v-leave-active {
  transition: .8s
}
</style>
