<template>
  <div class="title">
    <slot></slot>
  </div>
</template>
<style lang="scss" scoped>
.title {
  position: relative;
  display: inline-block;
  padding-bottom: 12px;
  margin-bottom: 15px;
  font-size: 26px;
  &::after {
    content: '';
    position: absolute;
    left: 0;
    bottom: 0;
    width: 40px;
    height: 2px;
    background-color: #fff;
  }
}
</style>
