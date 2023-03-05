<script setup></script>
<template>
  <a>
    <slot></slot>
  </a>
</template>
<style lang="scss" scoped>
a {
  display: inline-block;
  font-weight: 300;
  padding: 8px 40px;
  border: 1px solid rgba(#fff, 0.5);
  background-color: rgba(#fff, 0.15);
  color: #fff;
  font-size: 16px;
  letter-spacing: 0.05em;
  &:hover {
    background-color: #fff;
    color: #000;
  }
}
</style>
