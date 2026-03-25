<script setup lang="ts">
defineProps<{
  isOpen: boolean
}>()
defineEmits<{
  (e: 'toggle'): void
}>()
</script>

<template>
  <div class="filters-actions">
    <div class="recommended">
      <span>Рекомендованные</span>
      <svg width="12" height="7" viewBox="0 0 12 7" fill="none">
        <path d="M1 1L6 5L11 1" stroke="#0B1B3A" stroke-width="1.5" stroke-linecap="round"/>
      </svg>
    </div>
    <button class="all-filters" @click="$emit('toggle')">
      <span>Все фильтры</span>
      <svg width="12" height="7" viewBox="0 0 12 7" fill="none" :class="{ rotated: isOpen }">
        <path d="M1 1L6 5L11 1" stroke="#0B1B3A" stroke-width="1.5" stroke-linecap="round"/>
      </svg>
    </button>
  </div>
</template>

<style scoped>
.filters-actions {
  display: flex;
  gap: 20px;
  flex-shrink: 0;
}
.recommended,
.all-filters {
  display: flex;
  align-items: center;
  gap: 8px;
  background: #FFFFFF;
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 16px;
  font-weight: 500;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  cursor: pointer;
  transition: background 0.2s;
}
.recommended {
  background: #FFFFFF;
  box-shadow: 0 0 0 1px rgba(0,0,0,0.05);
}
.all-filters {
  background: rgba(73, 104, 148, 0.05);
}
.recommended:hover,
.all-filters:hover {
  background: rgba(73, 104, 148, 0.1);
}
.all-filters svg {
  transition: transform 0.2s;
}
.all-filters svg.rotated {
  transform: rotate(180deg);
}
</style>