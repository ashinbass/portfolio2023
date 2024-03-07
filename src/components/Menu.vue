<script setup>
import { RouterLink, useRoute } from 'vue-router'
import { ref } from 'vue'

const route = useRoute()

const menu = ref([
  {
    name: 'About',
    link: '/about'
  },
  {
    name: 'Work',
    link: '/work'
  }
])

const isShow = ref(false)

setTimeout(() => {
  isShow.value = true
}, 1000)
</script>
<template>
  <div class="menu" :class="{ show: isShow }">
    <RouterLink
      :to="item.link"
      v-for="(item, index) in menu"
      :key="index"
      :class="{ current: item.link == route.path }"
      >{{ item.name }}</RouterLink
    >
  </div>
</template>
<style lang="scss" scoped>
.menu {
  position: absolute;
  right: 50px;
  top: 40px;
  z-index: 2;
  transform: translateY(-15px);
  opacity: 0;
  transition: all 1s ease-in-out;
  @include max-media(767) {
    display: flex;
    justify-content: space-between;
    width: 100%;
    right: 20px;
  }
  &.show {
    transform: translateY(0);
    opacity: 1;
  }
  a {
    position: relative;
    color: #fff;
    font-weight: 400;
    font-size: 20px;
    letter-spacing: 0.2em;
    margin-left: 35px;
    text-transform: uppercase;
    @include max-media(480) {
      font-size: 16px;
    }
    &::after {
      content: '';
      position: absolute;
      left: 0;
      bottom: -8px;
      width: 0;
      height: 2px;
      background-color: #fff;
      transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);
    }
    &.current,
    &:hover {
      &::after {
        width: 100%;
      }
    }
  }
}
</style>
