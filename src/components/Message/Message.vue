<template>
  <transition name="fade">
    <div class="message" :class="type" v-show="show">
      <span class="text">{{ text }}</span>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'message',
  props: {
    type: {
      type: String,
      default: 'info',
      validator: val => ['info', 'success', 'warning', 'error'].includes(val)
      // ['info', 'success', 'warning', 'error'] 表示type只接收这四个字符串作为参数传入message组件
    },
    text: {
      type: String,
      default: ''
    },
    show: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped lang="less">
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.message {
  position: fixed;
  top: 40px;
  text-align: center;
  left: 50%;
  transform: translateX(-50%);
  min-width: 400px;
  padding: 10px 20px;
  color: #333333;
  background: #f5f5f5;
  font-size: 18px;
  line-height: 1.4;
  border-radius: 4px;
  z-index: 1000;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);

  &.info {
    color: purple;
  }

  &.success {
    color: green;
  }

  &.error {
    color: red;
  }

  &.warning {
    color: yellow;
  }
}
</style>
