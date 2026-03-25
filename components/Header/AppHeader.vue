<script setup lang="ts">
import { ref } from 'vue'

type NavItem = {
  name: string
  label: string
}

const navItems: NavItem[] = [
  { name: 'Главная', label: 'Главная' },
  { name: 'Каталог специалистов', label: 'Каталог специалистов' },
  { name: 'Блог', label: 'Блог' },
  { name: 'Специалистам', label: 'Специалистам' },
]

const activeItem = ref('Главная')
</script>

<template>
  <header class="header">
    <div class="header__container">
      <div class="header__top">
        <div class="header__search">
          <input type="text" placeholder="Поиск" class="search-input" />
          <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
            <path opacity="0.2" d="M10.0057 8.80503H9.37336L9.14923 8.58891C9.96085 7.64762 10.4069 6.44585 10.4059 5.20297C10.4059 4.17392 10.1008 3.16798 9.52909 2.31236C8.95738 1.45673 8.14478 0.789856 7.19407 0.396055C6.24335 0.00225437 5.1972 -0.100782 4.18792 0.099976C3.17865 0.300734 2.25157 0.796269 1.52392 1.52392C0.796269 2.25157 0.300734 3.17865 0.099976 4.18792C-0.100782 5.1972 0.00225437 6.24335 0.396055 7.19407C0.789856 8.14478 1.45673 8.95738 2.31236 9.52909C3.16798 10.1008 4.17392 10.4059 5.20297 10.4059C6.49171 10.4059 7.67639 9.93368 8.58891 9.14923L8.80503 9.37336V10.0057L12.8073 14L14 12.8073L10.0057 8.80503ZM5.20297 8.80503C3.20984 8.80503 1.60092 7.19611 1.60092 5.20297C1.60092 3.20984 3.20984 1.60092 5.20297 1.60092C7.19611 1.60092 8.80503 3.20984 8.80503 5.20297C8.80503 7.19611 7.19611 8.80503 5.20297 8.80503Z" fill="#0B1B3A"/>
          </svg>
        </div>
        <div class="header__logo">Практика</div>
        <div class="header__consult">
          <a href="tel:+79999999999">+7 999 999 99 99</a>
          <button class="consult-button">Бесплатная консультация</button>
        </div>
      </div>

      <nav class="header__nav">
        <div class="nav-list">
          <button
            v-for="item in navItems"
            :key="item.name"
            class="nav-link"
            :class="{ active: activeItem === item.name }"
            @click="activeItem = item.name"
          >
            {{ item.label }}
          </button>
        </div>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.header {
  background: #FFFFFF;
  width: 100%;
  position: relative;
}

.header__container {
  max-width: 1820px;
  margin: 0 auto;
  padding: 30px 50px 15px 50px;
}

.header__top {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
  margin-bottom: 24px;
}

.header__search {
  flex: 0 1 440px;
  min-width: 200px;
  background: rgba(11, 27, 58, 0.07);
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  gap: 10px;
}

.search-input {
  background: transparent;
  border: none;
  outline: none;
  font-size: 16px;
  line-height: 1;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  width: 100%;
}

.search-input::placeholder {
  color: rgba(11, 27, 58, 0.2);
}

.header__logo {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  font-family: 'Inter', sans-serif;
  font-size: clamp(32px, 5vw, 50px);
  line-height: 1;
  color: #0B1B3A;
  white-space: nowrap;
  pointer-events: none;
}

.header__consult {
  display: flex;
  gap: 20px;
  align-items: center;
  flex-wrap: wrap;
}

.header__consult a {
  font-weight: 500;
  font-size: 16px;
  line-height: 1;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  text-decoration: none;
  white-space: nowrap;
}

.consult-button {
  background: rgba(11, 27, 58, 0.07);
  border-radius: 20px;
  padding: 10px 20px;
  font-weight: 500;
  font-size: 16px;
  line-height: 1;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  cursor: pointer;
  transition: background 0.2s;
  border: none;
  white-space: nowrap;
}

.consult-button:hover {
  background: rgba(11, 27, 58, 0.15);
}

.header__nav {
  border-top: 1px solid rgba(11, 27, 58, 0.1);
  padding-top: 14px;
}

.nav-list {
  display: flex;
  justify-content: center;
  gap: 10px;
  flex-wrap: wrap;
}

.nav-link {
  background: none;
  border: none;
  font-weight: 500;
  font-size: 16px;
  line-height: 1;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  cursor: pointer;
  transition: color 0.2s, background 0.2s;
  padding: 5px 20px;
  border-radius: 50px;
}

.nav-link.active {
  background: #6598D9;
  color: #FFFFFF;
}

.nav-link:not(.active):hover {
  color: #6598D9;
}
</style>