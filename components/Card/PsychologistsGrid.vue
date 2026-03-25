<script setup lang="ts">
import type { Psychologist } from '~/types/psychologist'
import PsychologistCard from './components/PsychologistCard.vue'

defineProps<{
  psychologists: Psychologist[]
}>()
</script>

<template>
  <div class="grid">
    <PsychologistCard
      v-for="psych in psychologists"
      :key="psych.id"
      :psychologist="psych"
    />
  </div>
</template>

<style scoped>
.grid {
  background-color: #EEEEF1;
  max-width: 1820px;
  margin: 0 auto;
  padding: 10px 50px;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 20px;
}
</style>