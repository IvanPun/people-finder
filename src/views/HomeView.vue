<template>
  <div class="main">
    <div class="background-img" v-if="!searching">
      <img src="@/assets/images/background.jpg" alt="background" />
    </div>

    <div class="main-body">
      <div class="search-box">
        <search v-model="keyword" @change="handleInput"></search>

      </div>
      <ResultArea v-if="searching" :keyword="keyword"></ResultArea>
    </div>


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
  min-height: 100vh;
  padding: 5vh;

  /* 背景圖片 */
  /* background: url('@/assets/images/background.jpg') no-repeat center center, linear-gradient(#90A15B, #C0B099);
  background-size: contain;
  background-color: transparent; */
  background: linear-gradient(#90A15B, #C0B099);

  display: flex;
  flex-direction: column;
  align-items: center;

}

/* 半透明白色遮罩 */
.main::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.6);
  z-index: 5;
}

.background-img {
  position: absolute;
  top: 15vh;
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

.main-body {
  position: relative;
  z-index: 10;
}

.search-box {
  display: flex;
  justify-content: center;
}
</style>