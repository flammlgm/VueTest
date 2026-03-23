<script setup lang="ts">
import type { Psychologist } from '~/types/psychologist';

defineProps<{
  psychologist: Psychologist;
}>();
</script>

<template>
  <div class="card">
    <div class="card__image">
      <img :src="psychologist.imageUrl" :alt="psychologist.name" />
    </div>
    <div class="card__content">
      <h3 class="card__name">{{ psychologist.name }}</h3>
      <p class="card__description">{{ psychologist.description }}</p>
      <div class="card__footer">
        <div class="card__price">{{ psychologist.price }} руб.</div>
        <button class="card__button">Бесплатная консультация</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 440px;
  background: #FFFFFF;
  border-radius: 20px;
  overflow: hidden;
  transition: transform 0.2s, box-shadow 0.2s;
}
.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 24px rgba(0,0,0,0.1);
}
.card__image {
  height: 400px;
  background-color: #E5E5E5;
}
.card__image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.card__content {
  padding: 0 10px 10px 10px;
}
.card__name {
  font-family: 'Manrope', sans-serif;
  font-weight: 600;
  font-size: 22px;
  line-height: 100%;
  letter-spacing: 0.02em;
  color: #0B1B3A;
  margin: 20px 0 5px;
}
.card__description {
  font-weight: 300;
  font-size: 18px;
  line-height: 100%;
  letter-spacing: 0.02em;
  color: #0B1B3A;
  margin-bottom: 30px;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
.card__footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.card__price {
  font-family: 'Riviera', sans-serif;
  font-weight: 400;
  font-size: 40px;
  line-height: 100%;
  letter-spacing: -0.03em;
  color: #6598D9;
}
.card__button {
  background: rgba(11, 27, 58, 0.07);
  border-radius: 20px;
  padding: 10px 20px;
  font-weight: 500;
  font-size: 16px;
  line-height: 100%;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  cursor: pointer;
  transition: background 0.2s;
}
.card__button:hover {
  background: rgba(11, 27, 58, 0.15);
}
</style>