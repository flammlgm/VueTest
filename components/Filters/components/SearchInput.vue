<script setup lang="ts">
import { ref } from 'vue'

const searchQuery = ref('')
</script>

<template>
  <div class="search-input-wrapper">
    <input
      type="text"
      placeholder="Поиск"
      class="search-input"
      v-model="searchQuery"
    />
    <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path opacity="0.3" d="M10.0057 8.80503H9.37336L9.14923 8.58891C9.96085 7.64762 10.4069 6.44585 10.4059 5.20297C10.4059 4.17392 10.1008 3.16798 9.52909 2.31236C8.95738 1.45673 8.14478 0.789856 7.19407 0.396055C6.24335 0.00225437 5.1972 -0.100782 4.18792 0.099976C3.17865 0.300734 2.25157 0.796269 1.52392 1.52392C0.796269 2.25157 0.300734 3.17865 0.099976 4.18792C-0.100782 5.1972 0.00225437 6.24335 0.396055 7.19407C0.789856 8.14478 1.45673 8.95738 2.31236 9.52909C3.16798 10.1008 4.17392 10.4059 5.20297 10.4059C6.49171 10.4059 7.67639 9.93368 8.58891 9.14923L8.80503 9.37336V10.0057L12.8073 14L14 12.8073L10.0057 8.80503ZM5.20297 8.80503C3.20984 8.80503 1.60092 7.19611 1.60092 5.20297C1.60092 3.20984 3.20984 1.60092 5.20297 1.60092C7.19611 1.60092 8.80503 3.20984 8.80503 5.20297C8.80503 7.19611 7.19611 8.80503 5.20297 8.80503Z" fill="#0B1B3A"/>
    </svg>
  </div>
</template>

<style scoped>
.search-input-wrapper {
  max-width: 800px;
  width: 100%;
  background: #FFFFFF;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  gap: 10px;
  box-shadow: 0 0 0 1px rgba(0,0,0,0.05);
}
.search-input {
  width: 100%;
  border: none;
  outline: none;
  font-size: 16px;
  font-weight: 400;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  background: transparent;
}
.search-input::placeholder {
  color: rgba(11, 27, 58, 0.3);
  font-size: 16px;
}
</style>