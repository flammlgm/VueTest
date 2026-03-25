<script setup lang="ts">
import { ref, watch } from 'vue'

const props = defineProps<{
  isOpen: boolean
}>()

const emit = defineEmits<{
  (e: 'close'): void
}>()

watch(() => props.isOpen, (val) => {
  if (val) {
    document.body.style.overflow = 'hidden'
  } else {
    document.body.style.overflow = ''
  }
})

const close = () => {
  emit('close')
}

const openSections = ref({
  requests: true,
  approach: false,
  price: false,
  gender: false
})

const toggleSection = (section: keyof typeof openSections.value) => {
  openSections.value[section] = !openSections.value[section]
}

const approachOptions = ref([
  { id: 1, label: 'КПТ', checked: false },
  { id: 2, label: 'Гештальт', checked: false },
  { id: 3, label: 'Психоанализ', checked: false },
  { id: 4, label: 'Экзистенциальный', checked: false }
])

const priceOptions = ref([
  { id: 1, label: 'до 2000 ₽', checked: false },
  { id: 2, label: '2000–4000 ₽', checked: false },
  { id: 3, label: '4000–6000 ₽', checked: false },
  { id: 4, label: '6000–8000 ₽', checked: false },
  { id: 5, label: '8000+ ₽', checked: false }
])

const genderOptions = ref([
  { id: 1, label: 'Мужской', checked: false },
  { id: 2, label: 'Женский', checked: false }
])

const handleCheck = (category: string, id: number, checked: boolean) => {
  // console.log(`${category} ${id} = ${checked}`)
}
</script>

<template>
  <Teleport to="body">
    <Transition name="slide">
      <div v-if="isOpen" class="drawer">
        <div class="drawer__close">
          <button class="close-button" @click="close">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M15.5 4.5L4.5 15.5M4.5 4.5L15.5 15.5" stroke="#6598D9" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
          </button>
        </div>
        <div class="drawer__sections">
          <div class="section">
            <div class="section__header special" @click="toggleSection('requests')">
              <span class="section__title">Запросы</span>
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" :class="{ rotated: openSections.requests }">
                <path d="M5 7L10 12L15 7" stroke="white" stroke-width="2" stroke-linecap="round" />
              </svg>
            </div>
            <div v-show="openSections.requests" class="section__content">
              <label class="checkbox">
                <input type="checkbox" value="depression" />
                <span class="checkmark"></span>
                Депрессия
              </label>
              <label class="checkbox">
                <input type="checkbox" value="anxiety" />
                <span class="checkmark"></span>
                Тревожность
              </label>
              <label class="checkbox">
                <input type="checkbox" value="relations" />
                <span class="checkmark"></span>
                Отношения
              </label>
            </div>
          </div>

          <div class="section">
            <div class="section__header" @click="toggleSection('approach')">
              <span class="section__title">Подход</span>
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" :class="{ rotated: openSections.approach }">
                <path d="M5 7L10 12L15 7" stroke="#0B1B3A" stroke-width="2" stroke-linecap="round" />
              </svg>
            </div>
            <div v-show="openSections.approach" class="section__content">
              <label v-for="opt in approachOptions" :key="opt.id" class="checkbox">
                <input type="checkbox" v-model="opt.checked" @change="handleCheck('approach', opt.id, opt.checked)" />
                <span class="checkmark"></span>
                {{ opt.label }}
              </label>
            </div>
          </div>

          <div class="section">
            <div class="section__header" @click="toggleSection('price')">
              <span class="section__title">Цена</span>
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" :class="{ rotated: openSections.price }">
                <path d="M5 7L10 12L15 7" stroke="#0B1B3A" stroke-width="2" stroke-linecap="round" />
              </svg>
            </div>
            <div v-show="openSections.price" class="section__content">
              <label v-for="opt in priceOptions" :key="opt.id" class="checkbox">
                <input type="checkbox" v-model="opt.checked" @change="handleCheck('price', opt.id, opt.checked)" />
                <span class="checkmark"></span>
                {{ opt.label }}
              </label>
            </div>
          </div>

          <div class="section">
            <div class="section__header" @click="toggleSection('gender')">
              <span class="section__title">Пол</span>
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" :class="{ rotated: openSections.gender }">
                <path d="M5 7L10 12L15 7" stroke="#0B1B3A" stroke-width="2" stroke-linecap="round" />
              </svg>
            </div>
            <div v-show="openSections.gender" class="section__content">
              <label v-for="opt in genderOptions" :key="opt.id" class="checkbox">
                <input type="checkbox" v-model="opt.checked" @change="handleCheck('gender', opt.id, opt.checked)" />
                <span class="checkmark"></span>
                {{ opt.label }}
              </label>
            </div>
          </div>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>

<style scoped>
.drawer {
  position: fixed;
  top: 0;
  right: 0;
  width: 400px;
  height: 100vh;
  background: #EEEFF1;
  padding: 30px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  box-shadow: -2px 0 20px rgba(0, 0, 0, 0.1);
  z-index: 1100;
  overflow-y: auto;
}

.drawer__close {
  display: flex;
  justify-content: flex-end;
}

.close-button {
  width: 40px;
  height: 40px;
  background: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  border: none;
  transition: opacity 0.2s;
}
.close-button:hover {
  opacity: 0.8;
}
.close-button svg {
  display: block;
}

.drawer__sections {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.section {
  width: 100%;
}

.section__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  background: rgba(73, 104, 148, 0.05);
  border-radius: 20px;
  cursor: pointer;
  transition: background 0.2s;
}
.section__header.special {
  background: #0B1B3A;
}
.section__header.special .section__title {
  color: white;
}
.section__header:hover {
  background: rgba(73, 104, 148, 0.1);
}
.section__header.special:hover {
  background: #1a2e4e;
}

.section__title {
  font-weight: 600;
  font-size: 14px;
  line-height: 1;
  letter-spacing: 0.02em;
  color: #0B1B3A;
}
.section__header.special .section__title {
  color: white;
}

.section__header svg {
  transition: transform 0.3s ease;
}
.section__header svg.rotated {
  transform: rotate(180deg);
}

.section__content {
  margin-top: 10px;
  padding: 0 20px 10px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.checkbox {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 14px;
  font-weight: 400;
  letter-spacing: 0.02em;
  color: #0B1B3A;
  cursor: pointer;
  position: relative;
  user-select: none;
}
.checkbox input {
  position: absolute;
  opacity: 0;
  width: 0;
  height: 0;
}
.checkmark {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #FFFFFF;
  border: 1px solid #0B1B3A;
  transition: all 0.2s;
  display: inline-block;
  position: relative;
}
.checkbox input:checked + .checkmark {
  background: #0B1B3A;
  border-color: #0B1B3A;
}
.checkbox input:checked + .checkmark::after {
  content: '';
  position: absolute;
  left: 6px;
  top: 2px;
  width: 6px;
  height: 11px;
  border: solid white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}
.checkbox:hover .checkmark {
  border-color: #6598D9;
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 0.3s ease;
}
.slide-enter-from,
.slide-leave-to {
  transform: translateX(100%);
}
</style>