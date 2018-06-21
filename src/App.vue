<template>
  <div>
    <!--
    keep-alive组建缓存：https://cn.vuejs.org/v2/api/#keep-alive
    部分组件解除缓存方法：
    a. v-if配合keepAlive参数
    b. 使用include ／ exclude 组建名
    c. 组建内部在activated中重新发起请求
    -->
    <!-- a: v-if配合keepAlive示例
    <keep-alive>
      <router-view v-if="$route.meta.keepAlive"></router-view>
    </keep-alive>
    <router-view v-if="!$route.meta.keepAlive"></router-view>
    -->
    <keep-alive exclude="Detail">
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
