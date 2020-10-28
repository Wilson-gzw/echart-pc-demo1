<template>
  <div class="home">
    <top-view></top-view>
    <center-view></center-view>
    <bottom-view></bottom-view>
    <map-view></map-view>
  </div>
</template>

<script>
// @ is an alias to /src
import TopView from '@/components/top-view/index.vue'
import BottomView from '@/components/bottom-view/index.vue'
import CenterView from '@/components/center-view/index.vue'
import MapView from '@/components/map-view/index.vue'

export default {
  name: 'Home',
  components: {
    TopView, BottomView, CenterView, MapView
  }
}
</script>

<style lang="scss" scoped>
.home{
  width:100%;
  height:100%;
  padding: 20px;
  background: #eee;
  box-sizing: border-box;
}
</style>
