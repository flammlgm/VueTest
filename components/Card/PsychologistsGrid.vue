<script setup lang="ts">
import type { Psychologist } from '~/types/psychologist';

defineProps<{
  psychologists: Psychologist[];
}>();
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
  max-width: 1820px;
  margin: 0 auto;
  padding: 0 50px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  margin-bottom: 60px;
}
</style>