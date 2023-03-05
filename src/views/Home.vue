<script setup>
import { RouterLink } from 'vue-router'
import { onMounted, ref } from 'vue'

const isShow = ref(false)
onMounted(() => {
  setTimeout(() => {
    isShow.value = true
  }, 1000)
})
</script>

<template>
  <div class="home" :class="{ home__show: isShow }">
    <div class="home__bg"></div>
    <div class="home__box">
      <div class="home__hello">Hello<br />I am <span class="blue">Alvin</span></div>
      <div class="home__button">
        <RouterLink to="/about"><span>關於我</span></RouterLink>
        <RouterLink to="/work"><span>作品</span></RouterLink>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.blue {
  color: $blue;
}
.home {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
  background-color: #8c7e77;
  &__bg {
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    z-index: -1;
    background-image: url('@/assets/images/bg.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center bottom;
    opacity: 0.9;
  }
  &__box {
    width: 0;
    max-width: 600px;
    background-color: rgba(#fff, 0.1);
    backdrop-filter: blur(12px);
    box-shadow: 0 5px 20px rgba(#000, 0.008);
    overflow: hidden;
    transition: all 2s ease-in-out;
  }
  &__hello {
    padding: 35px 20px;
    line-height: 1.2;
    text-align: center;
    font-size: 50px;
    font-weight: 100;
    color: #fff;
    white-space: nowrap;
    opacity: 0;
    letter-spacing: 0.2em;
    filter: blur(5px);
    transform: scale(1.2);
    transition: all 1.2s ease-in-out;
  }
  &__button {
    position: relative;
    display: flex;
    &::before,
    &::after {
      content: '';
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      background-color: #fff;
      opacity: 0.25;
      transition: all 1.2s ease-in-out;
    }
    &::before {
      width: 0;
      height: 1px;
    }
    &::after {
      width: 1px;
      height: 0;
    }
    a {
      display: block;
      width: 50%;
      padding: 15px 20px;
      text-align: center;
      color: #fff;
      font-weight: 300;
      font-size: 20px;
      text-transform: uppercase;
      letter-spacing: 0.18em;
      white-space: nowrap;
      cursor: pointer;
      span {
        display: inline-block;
        opacity: 0;
        transform: translateY(8px);
        transition: opacity 1.2s ease-in-out, transform 1.2s ease-in-out;
        cursor: pointer;
      }
      &:hover {
        background-color: rgba(#fff, 0.75);
        color: $blue;
      }
    }
  }
  &__show {
    .home {
      &__box {
        width: 100%;
      }
      &__hello {
        opacity: 1;
        filter: blur(0);
        transform: scale(1);
        letter-spacing: 0em;
        transition-delay: .8s;
      }
      &__button {
        &::before {
          width: 100%;
          transition-delay: 1s;
        }
        &::after {
          height: 100%;
          transition-delay: 1.3s;
        }
        a {
          span {
            opacity: 1;
          transform: translateY(0);
          transition-delay: 1.8s;
          }
        }
      }
    }
  }
}
</style>
