<script setup lang="ts">
import { onMounted, ref } from 'vue'

const starVisible = ref(false)
const topVisible = ref(false)
const bottomVisible = ref(false)

onMounted(() => {
  setTimeout(() => {
    starVisible.value = true
  }, 500)
  setTimeout(() => {
    topVisible.value = true
  }, 1000)
  setTimeout(() => {
    bottomVisible.value = true
  }, 1500)
})
</script>

<template>
  <section class="hero">
    <div class="hero__background"></div>
    <div class="hero__content">
      <h1
        class="hero__title hero__title--top"
        :class="{ 'is-visible': topVisible }"
      >
        ПСИХОЛОГИ
      </h1>
      <div
        class="hero__star"
        :class="{ 'is-visible': starVisible }"
      >
        <svg width="590" height="590" viewBox="0 0 590 590" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M295 0L311.934 254.118L503.596 86.4035L335.882 278.066L590 295L335.882 311.934L503.596 503.596L311.934 335.882L295 590L278.066 335.882L86.4035 503.596L254.118 311.934L0 295L254.118 278.066L86.4035 86.4035L278.066 254.118L295 0Z" fill="#EEEADE" fill-opacity="0.5"/>
        </svg>
      </div>
      <h2
        class="hero__title hero__title--bottom"
        :class="{ 'is-visible': bottomVisible }"
      >
        ПРАКТИКИ
      </h2>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  width: 100%;
  max-width: 1920px;
  margin: 0 auto;
  height: 850px;
  background: linear-gradient(0deg, rgba(11, 27, 58, 0.2), rgba(11, 27, 58, 0.2));
  overflow: hidden;
}

.hero__background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('@/assets/images/hero-bg.png');
  background-size: cover;
  background-position: center bottom;
  z-index: 0;
}

.hero__content {
  position: relative;
  z-index: 1;
  height: 100%;
}

.hero__star {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 590px;
  height: 590px;
  pointer-events: none;
  opacity: 0;
  transition: opacity 0.6s cubic-bezier(0.2, 0.9, 0.4, 1.1);
}
.hero__star.is-visible {
  opacity: 1;
}

.hero__title {
  position: absolute;
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  font-size: 115px;
  line-height: 1;
  letter-spacing: 0.01em;
  margin: 0;
  padding: 0;
  white-space: nowrap;
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s cubic-bezier(0.2, 0.9, 0.4, 1.1),
              transform 0.6s cubic-bezier(0.2, 0.9, 0.4, 1.1);
}
.hero__title.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.hero__title--top {
  color: #FFFFFF;
  right: 50%;
  top: calc(50% - 295px); 
  text-align: right;
  transform-origin: right top;
}

.hero__title--bottom {
  color: #FFFFFF;
  left: 50%;
  bottom: calc(50% - 295px);
  text-align: left;
  transform-origin: left bottom;
}
</style>