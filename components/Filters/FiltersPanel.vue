<script setup lang="ts">
import { ref } from 'vue';

const filtersOpen = ref(false);

const toggleFilters = () => {
  filtersOpen.value = !filtersOpen.value;
};
</script>

<template>
  <div class="filters">
    <div class="filters__search">
      <input type="text" placeholder="Поиск" class="search-input" />
      <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
        <path d="M6.5 0C2.91015 0 0 2.91015 0 6.5C0 10.0899 2.91015 13 6.5 13C8.07973 13 9.53761 12.4741 10.7204 11.5857L13.2929 14.1582C13.6834 14.5487 14.3166 14.5487 14.7071 14.1582C15.0976 13.7677 15.0976 13.1345 14.7071 12.744L12.1346 10.1715C13.023 8.98868 13.5489 7.5308 13.5489 5.95107C13.5489 2.36123 10.6388 -0.548828 7.04895 -0.548828L6.5 0ZM6.5 2.5C8.70914 2.5 10.5 4.29086 10.5 6.5C10.5 8.70914 8.70914 10.5 6.5 10.5C4.29086 10.5 2.5 8.70914 2.5 6.5C2.5 4.29086 4.29086 2.5 6.5 2.5Z" fill="#0B1B3A" fill-opacity="0.3"/>
      </svg>
    </div>
    <div class="filters__tags">
      <button class="tag active">Все</button>
      <button class="tag">Семейные</button>
      <button class="tag">КПТ</button>
      <button class="tag">Сексологи</button>
      <button class="tag">Стресс</button>
      <button class="tag">Самооценка</button>
      <button class="tag">Недорогие</button>
      <button class="tag">Опытные</button>
    </div>
    <div class="filters__actions">
      <div class="recommended">
        <span>Рекомендованные</span>
        <svg width="12" height="7" viewBox="0 0 12 7" fill="none">
          <path d="M1 1L6 5L11 1" stroke="#0B1B3A" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
      </div>
      <button class="all-filters" @click="toggleFilters">
        <span>Все фильтры</span>
        <svg width="12" height="7" viewBox="0 0 12 7" fill="none" :class="{ rotated: filtersOpen }">
          <path d="M1 1L6 5L11 1" stroke="#0B1B3A" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
      </button>
    </div>
    <div v-if="filtersOpen" class="filters__extended">
      <!-- Здесь можно разместить дополнительные фильтры (чекбоксы, слайдеры) -->
      <div class="extended-filter">
        <h4>Специализация</h4>
        <label><input type="checkbox" /> Детский психолог</label>
        <label><input type="checkbox" /> Семейный психолог</label>
        <!-- и т.д. -->
      </div>
      <div class="extended-filter">
        <h4>Опыт работы</h4>
        <select>
          <option>от 1 года</option>
          <option>от 3 лет</option>
          <option>от 5 лет</option>
        </select>
      </div>
    </div>
  </div>
</template>


<style scoped>
.filters {
  max-width: 1820px;
  margin: 0 auto;
  padding: 0 50px;
  margin-top: 40px;
}

.filters__search {
  width: 900px;
  height: 50px;
  background: #FFFFFF;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  margin-bottom: 30px;
  box-shadow: 0px 0px 0px 1px rgba(0,0,0,0.05);
}
.search-input {
  width: 100%;
  border: none;
  outline: none;
  font-size: 26px;
  font-weight: 300;
  letter-spacing: 0.02em;
  color: #0B1B3A;
}
.search-input::placeholder {
  color: rgba(11, 27, 58, 0.3);
  font-size: 26px;
}

.filters__tags {
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
  margin-bottom: 30px;
}
.tag {
  font-size: 26px;
  font-weight: 300;
  letter-spacing: 0.02em;
  color: #0B1B3A;
  background: none;
  cursor: pointer;
  transition: color 0.2s;
}
.tag.active {
  background: #FFFFFF;
  border-radius: 50px;
  padding: 0 20px;
  height: 40px;
  line-height: 40px;
  background: #FFFFFF;
  box-shadow: 0 0 0 1px rgba(0,0,0,0.05);
}
.tag:hover {
  color: #6598D9;
}

.filters__actions {
  display: flex;
  justify-content: flex-end;
  gap: 30px;
  margin-bottom: 30px;
}
.recommended, .all-filters {
  display: flex;
  align-items: center;
  gap: 10px;
  background: #FFFFFF;
  padding: 10px 20px;
  border-radius: 20px;
  font-size: 26px;
  font-weight: 300;
  letter-spacing: 0.02em;
  color: #0B1B3A;
  cursor: pointer;
}
.recommended {
  background: #FFFFFF;
}
.all-filters {
  background: rgba(73, 104, 148, 0.05);
}
.recommended svg, .all-filters svg {
  transition: transform 0.2s;
}
.all-filters svg.rotated {
  transform: rotate(180deg);
}

.filters__extended {
  margin-top: 20px;
  padding: 20px;
  background: #F5F7FA;
  border-radius: 20px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
.extended-filter h4 {
  font-size: 18px;
  margin-bottom: 10px;
}
.extended-filter label {
  display: block;
  margin-bottom: 5px;
}
</style>