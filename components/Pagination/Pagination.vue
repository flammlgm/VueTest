<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  currentPage: number;
  totalPages: number;
}>();

const emit = defineEmits<{
  (e: 'pageChange', page: number): void;
}>();

const maxVisible = 5;

const visiblePages = computed(() => {
  const pages = [];
  let start = Math.max(1, props.currentPage - Math.floor(maxVisible / 2));
  let end = start + maxVisible - 1;
  if (end > props.totalPages) {
    end = props.totalPages;
    start = Math.max(1, end - maxVisible + 1);
  }
  for (let i = start; i <= end; i++) {
    pages.push(i);
  }
  return pages;
});

const showEllipsis = computed(() => {
  return props.totalPages > maxVisible && visiblePages.value[visiblePages.value.length - 1] < props.totalPages - 1;
});

const lastPage = computed(() => props.totalPages);

const changePage = (page: number) => {
  if (page >= 1 && page <= props.totalPages) {
    emit('pageChange', page);
  }
};
</script>

<template>
  <div class="pagination">
    <button class="pagination__arrow" :disabled="currentPage === 1" @click="changePage(currentPage - 1)">
      <svg width="8" height="15" viewBox="0 0 8 15" fill="none">
        <path d="M7 14L1 7.5L7 1" stroke="#0B1B3A" stroke-width="1.5" stroke-linecap="round"/>
      </svg>
    </button>
    <div class="pagination__numbers">
      <button v-for="page in visiblePages" :key="page" :class="{ active: page === currentPage }" @click="changePage(page)">
        {{ page }}
      </button>
      <span v-if="showEllipsis">...</span>
      <button v-if="lastPage > maxVisible" @click="changePage(lastPage)">{{ lastPage }}</button>
    </div>
    <button class="pagination__arrow" :disabled="currentPage === lastPage" @click="changePage(currentPage + 1)">
      <svg width="8" height="15" viewBox="0 0 8 15" fill="none">
        <path d="M1 1L7 7.5L1 14" stroke="#0B1B3A" stroke-width="1.5" stroke-linecap="round"/>
      </svg>
    </button>
  </div>
</template>

<style scoped>
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  margin: 60px 0;
}
.pagination__arrow {
  width: 40px;
  height: 40px;
  background: #FFFFFF;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background 0.2s;
}
.pagination__arrow:hover:not(:disabled) {
  background: #F0F0F0;
}
.pagination__arrow:disabled {
  opacity: 0.5;
  cursor: default;
}
.pagination__numbers {
  display: flex;
  gap: 10px;
  background: #FFFFFF;
  border-radius: 10px;
  padding: 5px 30px;
}
.pagination__numbers button {
  width: 30px;
  height: 30px;
  background: none;
  font-size: 18px;
  font-weight: 300;
  color: #0B1B3A;
  cursor: pointer;
  transition: background 0.2s, color 0.2s;
}
.pagination__numbers button.active {
  background: #0B1B3A;
  color: #FFFFFF;
  border-radius: 5px;
}
.pagination__numbers button:hover:not(.active) {
  color: #6598D9;
}
</style>