<script setup lang="ts">
import { ref } from 'vue'
import SearchInput from './components/SearchInput.vue'
import FiltersActions from './components/FiltersActions.vue'
import TagsList from './components/TagsList.vue'
import FiltersDrawer from './components/FiltersDrawer.vue'

const filtersOpen = ref(false)
const toggleFilters = () => {
  filtersOpen.value = !filtersOpen.value
}
</script>

<template>
  <div class="filters-panel">
    <div class="filters-panel__container">
      <div class="filters-panel__top">
        <SearchInput />
        <FiltersActions :is-open="filtersOpen" @toggle="toggleFilters" />
      </div>
      <TagsList />
    </div>
    <FiltersDrawer :is-open="filtersOpen" @close="filtersOpen = false" />
  </div>
</template>

<style scoped>
.filters-panel {
  background-color: #EEEEF1;
  width: 100%;
}
.filters-panel__container {
  max-width: 1820px;
  margin: 0 auto;
  padding: 40px 50px;
}
.filters-panel__top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
  margin-bottom: 30px;
}
</style>