<template>
  <footer class="footer">
    <div class="footer__cut footer__cut--left"></div>
    <div class="footer__cut footer__cut--right"></div>

    <div class="footer__star">
      <svg width="143" height="143" viewBox="0 0 143 143" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M71.5 0L81.6116 61.3884L143 71.5L81.6116 81.6116L71.5 143L61.3884 81.6116L0 71.5L61.3884 61.3884L71.5 0Z" fill="white"/>
      </svg>
    </div>

    <div class="footer__content">
      <div class="footer__top-texts">
        <div class="footer__text-left">
          <div class="footer__text-main">Психологи рядом</div>
          <div class="footer__text-sub">поддержка всегда доступна</div>
        </div>
        <div class="footer__text-right">
          <div class="footer__text-main">Помощь психолога онлайн</div>
          <div class="footer__text-sub">комфортно и конфиденциально</div>
        </div>
      </div>

      <div class="footer__button-wrapper">
        <button class="footer__button-center">Бесплатная консультация</button>
      </div>

      <nav class="footer__nav">
        <a href="#">Главная</a>
        <a href="#">Блог</a>
        <a href="#">Каталог специалистов</a>
        <a href="#">Специалистам</a>
      </nav>

      <div class="footer__info">
        <div class="footer__info-left">
          <div class="footer__contacts">
            <a href="tel:+79999999999" class="footer__phone">+7 999 999 99 99</a>
            <a href="mailto:practica@mail.com">practica@mail.com</a>
          </div>
          <div class="footer__policy">Политика конфиденциальности</div>
        </div>

        <div class="footer__info-center">
          <div class="footer__logo">Практика</div>
        </div>

        <div class="footer__info-right">
          <div class="footer__credits">
            <span>Разработка сайта</span>
            <span>Твой стартап</span>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  position: relative;
  width: 100%;
  background: #EEEEF1;
  margin-top: 0;
  overflow: hidden;
  min-height: 575px;
}

.footer__cut {
  position: absolute;
  top: 0;
  width: 50%;
  height: 100%;
  background: #496894;
  z-index: 1;
}
.footer__cut--left {
  left: 0;
  border-radius: 0 220px 0 0;
}
.footer__cut--right {
  right: 0;
  border-radius: 0 220px 0 0;
  transform: matrix(-1, 0, 0, 1, 0, 0);
}

.footer__star {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translate(-50%, 0);
  width: 120px;
  height: 120px;
  z-index: 2;
  pointer-events: none;
  display: flex;
  align-items: center;
  justify-content: center;
}
.footer__star svg {
  width: 100%;
  height: 100%;
  display: block;
}

.footer__content {
  position: relative;
  z-index: 3;
  max-width: 1820px;
  margin: 0 auto;
  padding: 100px 50px 0;
}

.footer__top-texts {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 80px;
}
.footer__text-left,
.footer__text-right {
  max-width: 505px;
}
.footer__text-main {
  font-family: 'Manrope', sans-serif;
  font-weight: 300;
  font-size: 28px;
  line-height: 1.2;
  letter-spacing: -0.03em;
  color: #FFFFFF;
  margin-bottom: 8px;
}
.footer__text-sub {
  font-family: 'Manrope', sans-serif;
  font-weight: 300;
  font-size: 28px;
  line-height: 1.2;
  letter-spacing: -0.03em;
  color: #B0CBE6;
}
.footer__text-right {
  text-align: right;
}
.footer__text-right .footer__text-sub {
  text-align: right;
}

.footer__button-wrapper {
  display: flex;
  justify-content: center;
  margin-bottom: 30px;
}
.footer__button-center {
  background: #FFFFFF;
  border-radius: 50px;
  padding: 16px 40px;
  font-weight: 500;
  font-size: 14px;
  line-height: 1;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  cursor: pointer;
  transition: background 0.2s;
  border: none;
  width: 550px;
}
.footer__button-center:hover {
  background: #F0F0F0;
}

.footer__nav {
  display: flex;
  justify-content: center;
  gap: 50px;
  margin-bottom: 20px;
  border-top: 1px solid #B0CBE6;
  border-bottom: 1px solid #B0CBE6;
  padding: 20px 0;
}
.footer__nav a {
  font-weight: 500;
  font-size: 16px;
  letter-spacing: -0.03em;
  color: #FFFFFF;
  text-decoration: none;
  transition: opacity 0.2s;
}
.footer__nav a:hover {
  opacity: 0.8;
}

.footer__info {
  display: flex;
  justify-content: space-between;
  align-items: stretch;
  margin-bottom: 40px;
  flex-wrap: wrap;
  gap: 20px;
}

.footer__info-left {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 20px;
}
.footer__contacts {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.footer__contacts a {
  font-weight: 500;
  font-size: 16px;
  letter-spacing: -0.03em;
  text-decoration: none;
}
.footer__phone {
  color: #A7ACB9;
}
.footer__contacts a:not(.footer__phone) {
  color: #FFFFFF;
}
.footer__policy {
  font-weight: 500;
  font-size: 16px;
  letter-spacing: -0.03em;
  color: #FFFFFF;
  text-decoration: none;
}

.footer__info-center {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: flex-start; 
}
.footer__logo {
  font-family: 'Inter', sans-serif;
  font-size: 35px;
  line-height: 100%;
  color: #FFFFFF;
}

.footer__info-right {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-end;
}
.footer__credits {
  text-align: left;
  font-family: 'Inter', sans-serif;
}
.footer__credits span:first-child {
  font-weight: 500;
  font-size: 16px;
  color: #B0CBE6;
  display: block;
  margin-bottom: 4px;
}
.footer__credits span:last-child {
  font-family: 'Inter', sans-serif;
  font-size: 40px;
  line-height: 100%;
  letter-spacing: -0.03em;
  text-transform: uppercase;
  color: #FFFFFF;
}

@media (max-width: 1200px) {
  .footer__top-texts {
    flex-direction: column;
    gap: 40px;
    margin-bottom: 60px;
  }
  .footer__text-right {
    text-align: left;
  }
  .footer__nav {
    flex-wrap: wrap;
    justify-content: center;
    gap: 30px;
  }
  .footer__info {
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 30px;
  }
  .footer__info-left,
  .footer__info-center,
  .footer__info-right {
    flex: auto;
    justify-content: center;
    text-align: center;
    width: 100%;
  }
  .footer__info-left {
    align-items: center;
  }
  .footer__contacts {
    align-items: center;
  }
  .footer__info-right {
    justify-content: center;
  }
  .footer__credits {
    text-align: center;
  }
}
</style>