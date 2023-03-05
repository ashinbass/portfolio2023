<script setup>
import { ref } from 'vue'

const logoTexts = ref(['P', 'o', 'r', 't', 'f', 'o', 'l', 'i', 'o'])
const isShow = ref(false)

setTimeout(() => {
  isShow.value = true
}, 1000)
</script>

<template>
  <div class="logo animation" :class="{ show: isShow }">
    <a href="./">
      <span v-for="(item, index) in logoTexts" :class="`text${index + 1}`">{{ item }}</span>
    </a>
  </div>
</template>

<style lang="scss" scoped>
.logo {
  position: absolute;
  left: 20px;
  top: 20px;
  z-index: 10;
  width: 120px;
  height: 133px;
  // background-image: url('../images/logo.jpg');
  background-color: rgba(#fff, 1);
  @include max-media(1180) {
    position: absolute;
    left: 50%;
    top: 20px;
    z-index: 5;
    transform-origin: left top;
    transform: scale(0.5) translateX(-50%);
  }
  a {
    position: relative;
    display: block;
    width: 100%;
    height: 100%;
    color: #000;
    font-size: 34px;
    font-weight: 400;
    line-height: 1;
    text-transform: uppercase;
  }
  span {
    position: absolute;
  }
  .text {
    &1 {
      left: 14px;
      top: 12px;
    }
    &2 {
      left: 45px;
      top: 12px;
    }
    &3 {
      left: 81px;
      top: 12px;
    }
    &4 {
      left: 15px;
      top: 49px;
    }
    &5 {
      left: 48px;
      top: 49px;
    }
    &6 {
      left: 80px;
      top: 49px;
    }
    &7 {
      left: 15px;
      top: 85px;
    }
    &8 {
      left: 52px;
      top: 85px;
    }
    &9 {
      left: 80px;
      top: 85px;
    }
  }
  &.animation {
    width: 0;
    height: 1px;
    span {
      opacity: 0;
      transform: scale(0.7);
      transition: 0.4s ease-in-out;
    }
    &.show {
      animation: logoWidthAnimation 0.4s ease-in-out both,
        logoHeightAnimation 0.4s 0.4s ease-in-out both;
      span {
        opacity: 1;
        transform: scale(1);
      }
      .text {
        &1 {
          transition-delay: 0.9s;
        }
        &2 {
          transition-delay: 1.2s;
        }
        &3 {
          transition-delay: 1.6s;
        }
        &4 {
          transition-delay: 1.1s;
        }
        &5 {
          transition-delay: 1.4s;
        }
        &6 {
          transition-delay: 1s;
        }
        &7 {
          transition-delay: 1.5s;
        }
        &8 {
          transition-delay: 1.7s;
        }
        &9 {
          transition-delay: 1.3s;
        }
      }
    }
  }
}

@keyframes logoWidthAnimation {
  0% {
    width: 0;
  }
  100% {
    width: 120px;
  }
}
@keyframes logoHeightAnimation {
  0% {
    height: 1px;
  }
  100% {
    height: 133px;
  }
}
</style>
