<template>
  <div class="app">
    <LeftNav></LeftNav>
    <div class="main">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import LeftNav from './components/common/leftNav.vue'

export default {
  mounted () {
    let mainWidth = document.body.clientWidth
    console.log(mainWidth)
  },
  components: {
    LeftNav
  }
}
</script>

<style lang="less" scoped>
.app {
  widows: 100%;
  height: 100%;

  .main {
    float: left;
    width: 95%;
  }
}
</style>
