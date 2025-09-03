<template>
  <div class="main" :class="searching ? 'bottom-blank' : ''">
    <div class="background-img">
      <img src="@/assets/images/background.jpg" alt="background" />
    </div>

    <!-- <div class="scroll-wrapper" :class="{ 'no-scroll': !searching }"> -->
      <div class="main-body">
        <div class="search-box">
          <search v-model="keyword" @change="handleInput"></search>

        </div>
        <ResultArea v-if="searching" :keyword="keyword"></ResultArea>
      </div>
    <!-- </div> -->



  </div>
</template>

<script setup>
import ResultArea from '@/components/ResultArea.vue';
import search from '@/components/search.vue';
import { ref } from 'vue';

const searching = ref(false);

const keyword = ref('')
const handleInput = (val) => {
  searching.value = val ? true : false
}
</script>

<style scoped>
.main {
  position: relative;
  width: 100%;
  height: 100%;

  /* 背景圖片 */
  /* background: url('@/assets/images/background.jpg') no-repeat center center, linear-gradient(#90A15B, #C0B099);
  background-size: contain;
  background-color: transparent; */

  display: flex;
  flex-direction: column;
  align-items: center;

}

.bottom-blank {
  padding-bottom: 5vh;
}

/* 半透明白色遮罩 */
.main::before {
  content: "";
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(255, 255, 255, 0.6);
  z-index: 5;
}

.background-img {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: center;
  z-index: 0;
}

.background-img img {
  width: 100%;
  height: auto;
  display: block;
}

.scroll-wrapper {
  width: 100%;
  height: 100%;
  overflow-y: auto;  /* 默認可滾動 */
}

.scroll-wrapper.no-scroll {
  overflow: hidden;   /* 禁止滾動 */
  touch-action: none; /* iOS防止手勢滾動 */
}


.main-body {
  position: relative;
  z-index: 10;
}

.search-box {
  display: flex;
  justify-content: center;
  margin-top: 5vh;
}
</style>