<script setup lang="ts">
import { ref } from 'vue'

const tags = ['Все', 'Семейные', 'КПТ', 'Сексологи', 'Стресс', 'Самооценка', 'Недорогие', 'Опытные']
const activeTag = ref('Все')
</script>

<template>
  <div class="tags-list">
    <button
      v-for="tag in tags"
      :key="tag"
      class="tag"
      :class="{ active: activeTag === tag }"
      @click="activeTag = tag"
    >
      {{ tag }}
    </button>
  </div>
</template>

<style scoped>
.tags-list {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}
.tag {
  font-size: 14px;
  font-weight: 500;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  background: none;
  padding: 3px 10px;
  border-radius: 50px;
  cursor: pointer;
  transition: background 0.2s, color 0.2s;
}
.tag.active {
  background: #FFFFFF;
  box-shadow: 0 0 0 1px rgba(0,0,0,0.05);
}
.tag:hover:not(.active) {
  background: rgba(11, 27, 58, 0.05);
}
</style>