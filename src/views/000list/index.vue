<template>
  <div class="main-content">
    <header-component :title="'模块功能列表'" :border="true" :instruction="'times'"></header-component>
    <ul class="main-list">
      <router-link v-for="item in list" :key="item.index" tag="li" :to="{ name: item.name }">{{ item.index }} - {{ item.intro }}</router-link>
    </ul>
  </div>
</template>

<script>
import { routes } from '@/router/routes'
export default {
  name: 'mainList',
  data() {
    return {
      list: routes.filter(i => i.index > 0)
    }
  }
}
</script>

<style lang="less" scoped>
.main-content {
  margin-top: 44px;
  transition: all 0.3s ease;
  overflow-y: scroll;
  .main-list {
    color: #1f2845; // 目录颜色
    li {
      height: 30px;
      line-height: 30px;
      padding: 6px 0 6px 18px;
      font-size: 18px;
      text-align: left;
      &:nth-child(odd) {
        background-color: #f8f8f8;
      }
      &:nth-child(even) {
        background-color: #f2f2f2;
      }
      &.active {
        background-color: #517df799; // 激活颜色
      }
    }
  }
}
</style>
