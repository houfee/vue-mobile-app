<template>
  <transition :name="transitionName">
    <keep-alive include="list">
      <router-view class="child-view"></router-view>
    </keep-alive>
  </transition>
</template>

<script>
export default {
  name: 'home',
  data() {
    return {
      transitionName: 'rightin'
    }
  },
  watch: {
    $route(to, from) {
      if(to.meta.index < from.meta.index) {
        this.transitionName = 'leftin'
      } else {
        this.transitionName = 'rightin'
      }
    }
  }
}
</script>

<style lang="less" scoped>
.rightin-enter,
.leftin-leave-active {
  opacity: 0;
  transform: translate3d(50% 0, 0);
  -webkit-transform: translate3d(50%, 0, 0);
  -moz-transform: translate3d(50%, 0, 0);
}
.leftin-enter,
.rightin-leave-active {
  opacity: 0;
  transform: translate3d(-50% 0, 0);
  -webkit-transform: translate3d(-50%, 0, 0);
  -moz-transform: translate3d(-50%, 0, 0);
}
</style>
