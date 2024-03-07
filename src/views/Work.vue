<script setup>
import { ref } from 'vue'
import Link from '@/components/Button/Link.vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation } from 'swiper'
import 'swiper/css'

const getImgUrl = (name) => {
  return new URL(name, import.meta.url).href
}
const workLists = [
  // {
  //   title: '歌唱大賽',
  //   list: ['＃全站網頁前端製作', '＃vue.js', '＃nuxt'],
  //   text: ``,
  //   link: 'https://singocac.tw/',
  //   bg: getImgUrl('../assets/images/work/singBg.jpg'),
  //   listImg: getImgUrl('../assets/images/work/sing.jpg'),
  //   isShow: true
  // },
  {
    title: 'IW 傢飾',
    list: ['＃全站網頁前端製作', '＃vue.js', '＃nuxt'],
    text: ``,
    link: 'https://www.iw-space.com/',
    bg: getImgUrl('../assets/images/work/iwBg.jpg'),
    listImg: getImgUrl('../assets/images/work/iw.jpg'),
    isShow: true
  },
  {
    title: 'CTS',
    list: ['＃全站網頁前端製作', '＃vue.js'],
    text: ``,
    link: 'https://www.ctsystem.com/en/',
    bg: getImgUrl('../assets/images/work/ctsBg.jpg'),
    listImg: getImgUrl('../assets/images/work/cts.jpg'),
    isShow: true
  },
  {
    title: 'ALUXE 亞立詩',
    list: ['＃全站網頁前端製作', '＃與後端工程師合作開發網站', '＃PHP、MySQL'],
    text: ``,
    link: 'https://www.aluxe.com/',
    bg: getImgUrl('../assets/images/work/aluxeBg.jpg'),
    listImg: getImgUrl('../assets/images/work/aluxe.jpg'),
    isShow: true
  },
  {
    title: '板橋凱撒大飯店',
    list: ['＃全站網頁前端製作', '＃串接訂房api', '＃PHP、MySQL'],
    text: `首頁banner人物是由同事設計繪製，網站開發時已拿到完成的gif檔。<br>依照每張gif的動畫，使用css animation搭配適合的移動速率，讓他可以在行走時候確實的一步一步的行走而非有太奇怪的躍動感`,
    link: 'https://banqiao.caesarpark.com.tw/',
    bg: getImgUrl('../assets/images/work/caesarparkBg.jpg'),
    listImg: getImgUrl('../assets/images/work/caesarpark.jpg'),
    isShow: true
  },
  {
    title: 'MML',
    list: ['＃全站網頁前端製作', '＃與後端工程師合作開發網站', '＃PHP、MySQL'],
    text: `網頁使用大量大圖及滾動式差營造出大器感<br>
            banner按鈕使用svg畫圓，搭配animationend達到動畫結束切換slider<br>
            首頁頁尾點擊直營門市，利用session storage紀錄資訊，進入內頁後切換slider呈現對應門市方便使用者查看，並利用ajax撈出銷售據點`,
    link: 'https://www.mymml.com.tw/',
    bg: getImgUrl('../assets/images/work/mmlBg.jpg'),
    listImg: getImgUrl('../assets/images/work/mml.jpg'),
    isShow: false
  },
  {
    title: '燒肉同話',
    list: ['＃全站網頁前端製作', '＃PHP、MySQL'],
    text: `loading使用particles.js營造出火花效果<br>
            banner利用canvas plugin，搭配圖片遮罩，讓使用者彷彿置身於餐桌現場烤肉`,
    link: 'https://www.chagether.com.tw/',
    bg: getImgUrl('../assets/images/work/chagetherBg.jpg'),
    listImg: getImgUrl('../assets/images/work/chagether.jpg'),
    isShow: false
  },
  {
    title: '茶之魔手',
    list: ['＃全站網頁前端製作', '＃PHP、MySQL'],
    text: `最新消息使用lightbox搭配ajax撈出文章資訊，並於網站加入css animation動畫增添網頁豐富度`,
    link: 'https://www.teamagichand.com.tw/',
    bg: getImgUrl('../assets/images/work/teamagichandBg.jpg'),
    listImg: getImgUrl('../assets/images/work/teamagichand.jpg'),
    isShow: false
  },
  {
    title: '日月潭湖悅',
    list: ['＃全站網頁前端製作', '＃PHP、MySQL'],
    text: `根據設計稿製作網站版型，並調整網頁整體動畫速率呈現優雅風格`,
    link: 'https://www.huyue.com.tw/',
    bg: getImgUrl('../assets/images/work/huyueBg.jpg'),
    listImg: getImgUrl('../assets/images/work/huyue.jpg'),
    isShow: false
  },
  {
    title: '漢來大飯店',
    list: ['＃全站網頁前端製作', '#串接訂房api、天氣api、google map api', '＃PHP、MySQL'],
    text: `推薦行程串接google map，並利用php處理將資料庫行程資料轉為JSON格式，利用js跑迴圈將景點渲染到地圖上`,
    link: 'https://www.grand-hilai.com/',
    bg: getImgUrl('../assets/images/work/hilaiBg.jpg'),
    listImg: getImgUrl('../assets/images/work/hilai.jpg'),
    isShow: false
  }
]
const activeIndex = ref(0)

const onSlideChange = (swiper) => {
  // console.log(swiper)
  activeIndex.value = swiper.realIndex
}

const modules = [Navigation]
</script>
<template>
  <ul class="workBgList">
    <li v-for="(item, index) in workLists" :class="{ current: activeIndex == index }" :key="index">
      <img :src="item.bg" />
    </li>
  </ul>
  <section class="work">
    <div class="work__leftBox">
      <ul class="work__info">
        <li
          v-for="(item, index) in workLists"
          :class="{ current: activeIndex == index }"
          :key="index"
        >
          <div class="title">{{ item.title }}</div>
          <div class="subtitle">參與製作項目</div>
          <ul class="listItem" v-for="list in item.list">
            <li>{{ list }}</li>
          </ul>
          <div class="text" v-html="item.text"></div>
          <div class="btn1">
            <Link :href="item.link" target="_blank">前往網站</Link>
          </div>
        </li>
      </ul>
    </div>
    <div class="work__rightBox">
      <swiper
        :modules="modules"
        :slides-per-view="2"
        :space-between="0"
        :loop="true"
        :slideToClickedSlide="true"
        :breakpoints="{
          768: {
            slidesPerView: 4
          },
          641: {
            slidesPerView: 3
          }
        }"
        :navigation="{ nextEl: '.nextArrow', prevEl: '.prevArrow' }"
        class="work__list"
        @slideChange="onSlideChange"
      >
        <swiper-slide v-for="(item, index) in workLists" :key="index">
          <div class="box">
            <div class="pic"><img :src="item.listImg" /></div>
            <div class="title">{{ item.title }}</div>
          </div>
        </swiper-slide>
      </swiper>
      <div class="work__arrow">
        <button class="arrows prevArrow"><img src="@/assets/arrow.svg" alt="" /></button>
        <button class="arrows nextArrow"><img src="@/assets/arrow.svg" alt="" /></button>
      </div>
    </div>
  </section>
</template>
<style lang="scss" scoped>
.work {
  position: relative;
  display: flex;
  width: 100%;
  margin-top: 330px;
  padding-bottom: 50px;
  overflow: hidden;
  @include max-media(1180) {
    margin-top: 150px;
    flex-wrap: wrap;
  }
  &__leftBox {
    width: 40%;
    padding-left: 50px;
    padding-right: 80px;
    @include max-media(1180) {
      width: 100%;
      padding-left: 20px;
      padding-right: 20px;
      padding-bottom: 50px;
    }
  }
  &__rightBox {
    width: 60%;
    @include max-media(1180) {
      width: 100%;
    }
  }
  .arrowBox {
    width: 100%;
    padding-top: 30px;
    .arrows {
      margin-right: 10px;
    }
  }
  &__list {
    margin-left: -15px;
    margin-right: -15px;
    @include min-media(1181) {
      width: calc(100% + (100% / 4));
    }
    @include max-media(1180) {
      width: calc(100% + (100% / 5));
      padding-left: 20px;
    }
    @include max-media(767) {
      margin-left: -8px;
      margin-right: -8px;
    }
    @include max-media(640) {
    }
    .swiper-slide {
      position: relative;
      display: inline-block;
      width: 25%;
      padding-left: 15px;
      padding-right: 15px;
      cursor: pointer;
      @include max-media(767) {
        padding-left: 8px;
        padding-right: 8px;
      }
      &:hover {
        @include min-media(1181) {
          .pic {
            opacity: 1;
          }
        }
      }
    }
    .swiper-slide-active {
      .pic {
        opacity: 1;
      }
    }
    .box {
      position: relative;
      background-color: #000;
      max-width: 320px;
      margin-left: auto;
      margin-right: auto;
    }
    .pic {
      opacity: 0.5;
      @include transition(0.8s);
      img {
        display: block;
        width: 100%;
      }
    }
    .title {
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      padding: 15px 20px;
      background-color: rgba(#0d1a26, 0.9);
      font-size: 20px;
      letter-spacing: 0.05em;
      font-weight: 300;
      color: #fff;
      @include max-media(767) {
        padding: 12px;
        font-size: 16px;
      }
    }
  }
  &__arrow {
    padding-top: 20px;
    .arrows {
      position: relative;
      display: inline-block;
      width: 50px;
      height: 50px;
      // border: 1px solid #fff;
      border-radius: 50%;
      background: none;
      border: none;
      cursor: pointer;
      &.prevArrow {
        img {
          transform: scaleX(-1);
        }
      }
      &:hover {
        &.prevArrow {
          img {
            transform: scaleX(-1) translateX(5px);
          }
        }
        &.nextArrow {
          img {
            transform: translateX(5px);
          }
        }
      }
    }
    img {
      position: absolute;
      left: 50%;
      top: 50%;
      margin-top: -13px;
      margin-left: -13px;
      display: block;
      width: 26px;
      height: 26px;
      @include transition;
    }
  }
  &__info {
    color: #fff;
    letter-spacing: 0.05em;
    font-weight: 300;
    list-style-type: none;
    padding: 0;
    > li {
      display: none;
    }
    .current {
      display: block;
    }
    .title {
      padding-bottom: 20px;
      font-size: 42px;
      letter-spacing: 0.1em;
      @include max-media(480) {
        font-size: 36px;
        padding-bottom: 12px;
      }
    }
    .subtitle {
      position: relative;
      display: inline-block;
      // padding-top: 30px;
      padding-right: 30px;
      // margin-top: 10px;
      margin-bottom: 15px;
      font-size: 24px;
      &::before,
      &::after {
        content: '';
        position: absolute;
        right: 0;
        top: 50%;
        margin-top: -0.5px;
        width: 18px;
        height: 1px;
        background-color: #fff;
      }
      &::before {
        transform: rotate(45deg);
      }
      &::after {
        transform: rotate(-45deg);
      }
      // &::before,
      // &::after {
      //     content: '';
      //     position: absolute;
      //     left: 10px;
      //     top: 0;
      //     width: 30px;
      //     height: 1px;
      //     background-color: #fff;
      // }
      // &::before {
      //     transform: rotate(45deg);
      // }
      // &::after {
      //     transform: rotate(-45deg);
      // }
    }
    .listItem {
      width: 100%;
      margin-bottom: 10px;
      font-size: 20px;
      list-style-type: none;
      padding: 0;
      line-height: 1;
      li {
        padding-bottom: 5px;
      }
    }
    .text {
      margin-bottom: 20px;
      font-size: 17px;
      color: #dadada;
      line-height: 1.7;
    }
  }
}
.workBgList {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  background-color: #000;
  li {
    position: absolute;
    left: 0;
    top: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: all 1s ease-in-out;
    &.current {
      opacity: 1;
      img {
        transform: scale(1);
        transition: all 1s ease-in-out;
      }
    }
  }
  img {
    display: block;
    width: 100%;
    height: 100vh;
    object-fit: cover;
    opacity: 0.5;
    transform: scale(1.1);
    transform-origin: center;
    transition: all 0.5s ease-in-out;
  }
}
</style>
