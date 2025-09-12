<template>
  <div class="main">
    <div class="background-img">
      <img src="@/assets/images/background.jpg" alt="background" />
    </div>

    <!-- <div class="scroll-wrapper" :class="{ 'no-scroll': !searching }"> -->
    <div class="main-body bottom-blank">
      <div class="search-box">
        <search v-model="keyword" @change="handleInput"></search>

      </div>
      <ResultArea :keyword="keyword"></ResultArea>
    </div>
    <!-- </div> -->
    <transition name="fade">
      <button v-show="showBtn" class="back-to-top" @click="scrollToTop"><el-icon><CaretTop /></el-icon></button>
    </transition>
  </div>

</template>

<script setup>
import ResultArea from '@/components/ResultArea.vue';
import search from '@/components/search.vue';
import { ref, onMounted } from 'vue';
import { CaretTop } from '@element-plus/icons-vue'

const searching = ref(false);

const keyword = ref('')
const handleInput = (val) => {
  searching.value = val ? true : false
}

const showBtn = ref(false);

const handleScroll = () => {
  showBtn.value = window.scrollY > 200;
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};

onMounted(() => {
  const el = document.querySelector(".scroll-wrapper") || window;
  el.addEventListener("scroll", handleScroll);
});
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
  background-color: rgba(255, 255, 255, 0.5);
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
  overflow-y: auto;
  /* 默認可滾動 */
}

.scroll-wrapper.no-scroll {
  overflow: hidden;
  /* 禁止滾動 */
  touch-action: none;
  /* iOS防止手勢滾動 */
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

/* back to top btn */

/* 進出場的過渡效果 */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s ease;
}

/* 進場前 & 離場後的狀態 */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.back-to-top {
  position: fixed;
  bottom: 40px;
  right: 1rem;
  background-color: #94a7ae;
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 24px;
  cursor: pointer;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
  transition: opacity 0.5s ease;
  z-index: 9999;
}
</style>