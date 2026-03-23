<script setup lang="ts">
import { ref, computed } from 'vue';
import type { Psychologist } from '~/types/psychologist';

import AppHeader from '@/components/Header/AppHeader.vue';
import HeroSection from '@/components/Hero/HeroSection.vue';
import FiltersPanel from '@/components/Filters/FiltersPanel.vue';
import PsychologistsGrid from '@/components/Card/PsychologistsGrid.vue';
import Pagination from '@/components/Pagination/Pagination.vue';
import AppFooter from '@/components/Footer/AppFooter.vue';

const allPsychologists: Psychologist[] = [
  {
    id: 1,
    name: 'Соколова Александра Владимировна',
    description: 'Специалист по детско-родительским отношениям, помогает справляться с тревожностью и выстраивать доверие в семье.',
    price: 5150,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+1',
  },
  {
    id: 2,
    name: 'Иванова Мария Петровна',
    description: 'Семейный психолог, гештальт-терапевт. Опыт работы 12 лет. Помогает парам в кризисных ситуациях.',
    price: 4800,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+2',
  },
  {
    id: 3,
    name: 'Кузнецов Дмитрий Андреевич',
    description: 'КПТ-терапевт, специалист по тревожным расстройствам и паническим атакам. Работает онлайн.',
    price: 5500,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+3',
  },
  {
    id: 4,
    name: 'Петрова Елена Сергеевна',
    description: 'Психолог-сексолог, эксперт по вопросам интимной жизни и партнёрских отношений. Бережный подход.',
    price: 6000,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+4',
  },
  {
    id: 5,
    name: 'Смирнов Алексей Викторович',
    description: 'Клинический психолог, работа с последствиями травм и ПТСР. Индивидуальный подход к каждому.',
    price: 5300,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+5',
  },
  {
    id: 6,
    name: 'Козлова Анна Игоревна',
    description: 'Детский психолог, игровая терапия. Помогает детям от 3 до 12 лет справляться со страхами и адаптироваться в коллективе.',
    price: 4900,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+6',
  },
  {
    id: 7,
    name: 'Морозов Иван Павлович',
    description: 'Психолог-консультант, специализация – профориентация и карьерные кризисы. Помогает найти своё призвание.',
    price: 4700,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+7',
  },
  {
    id: 8,
    name: 'Новикова Ольга Владимировна',
    description: 'Арт-терапевт, работа с эмоциональными состояниями через творчество. Подходит для тех, кому сложно выразить чувства словами.',
    price: 5200,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+8',
  },
  {
    id: 9,
    name: 'Васильев Николай Дмитриевич',
    description: 'Экзистенциальный терапевт, помогает в поиске смысла и преодолении возрастных кризисов.',
    price: 5400,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+9',
  },
  {
    id: 10,
    name: 'Захарова Татьяна Алексеевна',
    description: 'Семейный системный терапевт. Работа с конфликтами, созависимостью, выстраиванием личных границ.',
    price: 5900,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+10',
  },
  {
    id: 11,
    name: 'Волков Артём Сергеевич',
    description: 'Спортивный психолог, подготовка к соревнованиям, работа с мотивацией и преодолением стресса.',
    price: 5100,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+11',
  },
  {
    id: 12,
    name: 'Фёдорова Екатерина Павловна',
    description: 'Психолог по пищевому поведению, помогает справиться с РПП и выстроить здоровые отношения с едой.',
    price: 5700,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+12',
  },
  {
    id: 13,
    name: 'Григорьев Максим Олегович',
    description: 'Когнитивно-поведенческий терапевт, работа с ОКР, фобиями и навязчивыми мыслями.',
    price: 6200,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+13',
  },
  {
    id: 14,
    name: 'Михайлова Дарья Андреевна',
    description: 'Гештальт-терапевт, работа с незавершёнными ситуациями, поиск внутренних ресурсов.',
    price: 5000,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+14',
  },
  {
    id: 15,
    name: 'Степанов Олег Викторович',
    description: 'Психолог-консультант, эксперт по вопросам самооценки и личностного роста. Групповые и индивидуальные сессии.',
    price: 5300,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+15',
  },
  {
    id: 16,
    name: 'Александрова Юлия Сергеевна',
    description: 'Юнгианский аналитик, работа с архетипами, сновидениями, глубинными слоями психики.',
    price: 6500,
    imageUrl: 'https://via.placeholder.com/440x400?text=Psychologist+16',
  },
];

const itemsPerPage = 4; 
const currentPage = ref(1);

const totalPages = computed(() => Math.ceil(allPsychologists.length / itemsPerPage));

const paginatedPsychologists = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  const end = start + itemsPerPage;
  return allPsychologists.slice(start, end);
});

const handlePageChange = (page: number) => {
  currentPage.value = page;
  window.scrollTo({ top: 0, behavior: 'smooth' });
};
</script>

<template>
  <div class="catalog-page">
    <AppHeader />
    <HeroSection />
    <!-- <FiltersPanel />
    <PsychologistsGrid :psychologists="paginatedPsychologists" />
    <Pagination
      :current-page="currentPage"
      :total-pages="totalPages"
      @page-change="handlePageChange"
    />
    <AppFooter /> -->
  </div>
</template>

<style scoped>
.catalog-page {
  max-width: 1920px;
  margin: 0 auto;
  position: relative;
}
</style>
