<script setup>
import { ref } from 'vue'
import MainTitle from '@/components/Title/MainTitle.vue'

const skill = ref([
  {
    title: 'Front-end',
    list: [
      'HTML',
      'CSS / SCSS',
      'RWD',
      'JavaScript / Vue / jQuery',
      'AJAX / JSON',
      'API',
      'Git',
      'Cypress',
      'Vitest',
      'vue-test-utils'
    ]
  },
  {
    title: 'Back-end',
    list: ['PHP', 'MySQL']
  }
])

const job = ref([
  {
    company: '中佑資訊有限公司',
    jobTitle: '前端工程師',
    startTime: '2021 / 6',
    endTime: '仍在職',
    list: [
      '個人獨立製作專案',
      '專案管理系統、登入紀錄、監控系統、報表資料串接並視覺化',
      '業主系統網站改版升級，從 jQuery 升級至 vue3',
      '與PM、UI設計師及後端工程師，討論專案需求及製作',
      '前端畫面實現',
      '後端API串接',
      'e2e自動化測試',
      'vitest 單元測試',
      '維護現有專案'
    ]
  },
  {
    company: '愛貝斯網路',
    jobTitle: '前端工程師',
    startTime: '2016 / 9',
    endTime: '2021 / 5',
    list: [
      '個人獨立製作專案',
      '為網站細節加上互動元素與動畫，增加使用者體驗',
      '根據設計稿製作網站版型，加入 RWD 設計製作符合各個裝置的排版',
      '使用 PHP 和 MySQL 處理後端資料',
      '使用 ajax 接收 server 資料',
      '製作公司官方網站',
      '網頁SEO優化',
      '客戶網站上線',
      '維護舊專案',
      '協助新進人員了解工作項目'
    ]
  },
  {
    company: '向上國際科技',
    jobTitle: '前端設計師',
    startTime: '2016 / 5',
    endTime: '2016 / 8',
    list: [
      '根據設計稿製作網站版型，加入RWD設計製作符合各個裝置的排版',
      '協助設計師製作各平台廣告圖',
      '維護官網活動網頁',
      '活動網站資料上架'
    ]
  },
  {
    company: '鎂奈互動設計',
    jobTitle: '網頁設計師',
    startTime: '2015 / 11',
    endTime: '2016 / 4',
    list: ['依照客戶需求設計版型及切版', '製作公司官方網站']
  },
  {
    company: '杰鼎數位科技',
    jobTitle: '網頁設計師',
    startTime: '2013 / 3',
    endTime: '2015 / 10',
    list: ['依照客戶需求設計版型及切版', 'Flash 動畫製作', '維護舊專案', '與客戶溝通']
  }
])
</script>

<template>
  <div class="about">
    <div class="about__bg"></div>
    <div class="about__content">
      <div class="about__inner">
        <div class="about__photo">
          <img src="@/assets/images/me2.jpg" alt="" />
        </div>
        <div class="about__bottom">
          <div class="about__me">
            <div class="about__me__name">劉家瑋</div>
            <a href="mailto:dreamboat555@gmail.com" class="about__me__mail"
              >dreamboat555@gmail.com</a
            >
            <MainTitle class="about__mainTitle">技能</MainTitle>
            <ul class="about__skill">
              <li v-for="(item, index) in skill" :key="index">
                <div class="title">{{ item.title }}</div>
                <div class="text" v-for="(list, listIndex) in item.list" :key="listIndex">
                  <p>{{ list }}</p>
                </div>
              </li>
            </ul>
          </div>
          <MainTitle class="about__mainTitle">工作經歷</MainTitle>
          <div class="about__history" v-for="(item, index) in job" :key="index">
            <div class="about__history__title">{{ item.company }} - {{ item.jobTitle }}</div>
            <div class="about__history__time">{{ item.startTime }} ~ {{ item.endTime }}</div>
            <ul
              class="about__history__list"
              v-for="(list, listIndex) in item.list"
              :key="listIndex"
            >
              <li>{{ list }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@keyframes moveStar {
  0% {
    background-position-x: 0;
  }
  100% {
    background-position-x: -3840px;
  }
}
.about {
  position: relative;
  z-index: 1;
  display: flex;
  justify-content: center;
  width: 100%;
  height: 100vh;
  background-color: $blue;
  overflow-y: auto;
  &__bg {
    position: fixed;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    z-index: -1;
    background-image: url('../assets/images/about/bg.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    &::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-image: url('../assets/images/about/star.png');
      background-repeat: repeat-x;
      animation: moveStar 200s infinite linear;
    }
  }
  &__inner {
    width: 100%;
    max-width: 800px;
    margin-top: 30px;
    margin-left: auto;
    margin-right: auto;
  }
  &__content {
    position: relative;
    width: 100%;
    color: #fff;
    font-size: 20px;
    font-weight: 300;
    letter-spacing: 0.1em;
  }
  &__bottom {
    margin-top: -50px;
    background-color: rgba(#fff, 0.06);
    backdrop-filter: blur(7px);
    padding: 65px 30px 20px;
  }
  &__photo {
    position: relative;
    z-index: 2;
    width: 100px;
    height: 100px;
    margin-left: auto;
    margin-right: auto;
    border-radius: 50%;
    overflow: hidden;
    border: 1px solid #fff;
    img {
      display: block;
      width: 100%;
    }
  }
  &__me {
    display: flex;
    flex-direction: column;
    align-items: center;
    &__name {
      font-size: 26px;
      text-align: center;
    }
    &__mail {
      position: relative;
      display: inline-block;
      margin-bottom: 20px;
      font-size: 16px;
      color: #fff;
      &::after {
        content: '';
        position: absolute;
        left: 0;
        bottom: 0;
        width: 100%;
        height: 1px;
        background-color: #fff;
        opacity: 0.5;
      }
    }
  }
  &__mainTitle {
    width: 100%;
  }
  &__skill {
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    margin-bottom: 30px;
    margin-left: -5px;
    margin-right: -5px;
    list-style: none;
    padding: 0;
    li {
      width: 50%;
      padding-left: 5px;
      padding-right: 5px;
      @include max-media(640) {
        width: 100%;
        margin-bottom: 15px;
      }
    }
    .title {
      font-weight: 400;
      font-size: 22px;
      margin-bottom: 7px;
    }
    .text {
      color: #ddd;
      font-size: 16px;
    }
  }
  &__history {
    &:not(:last-child) {
      margin-bottom: 25px;
      padding-bottom: 25px;
      border-bottom: 1px solid rgba(#fff, 0.1);
    }
    &__title {
      font-size: 18px;
    }
    &__time {
      margin-bottom: 12px;
      font-size: 16px;
      color: #ddd;
    }
    &__list {
      list-style: none;
      li {
        position: relative;
        padding-left: 16px;
        font-size: 15px;
        &::before {
          content: '';
          position: absolute;
          left: 0;
          top: 13px;
          width: 6px;
          height: 1px;
          background-color: #fff;
        }
      }
    }
  }
}
</style>
