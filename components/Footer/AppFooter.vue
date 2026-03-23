<template>
  <footer class="footer">
    <div class="footer__left"></div>
    <div class="footer__right"></div>
    <div class="footer__content">
      <div class="footer__top">
        <div class="footer__text-left">Психологи рядом <br />поддержка всегда доступна</div>
        <div class="footer__button-center">Бесплатная консультация</div>
        <div class="footer__text-right">Помощь психолога онлайн <br />комфортно и конфиденциально</div>
      </div>
      <div class="footer__middle">
        <nav class="footer__nav">
          <a href="#">Главная</a>
          <a href="#">Блог</a>
          <a href="#">Каталог специалистов</a>
          <a href="#">Специалистам</a>
        </nav>
        <div class="footer__contacts">
          <a href="tel:+79999999999">+7 999 999 99 99</a>
          <a href="mailto:practica@mail.com">practica@mail.com</a>
        </div>
        <div class="footer__logo">Практика</div>
      </div>
      <div class="footer__bottom">
        <a href="#" class="footer__policy">Политика конфиденциальности</a>
        <div class="footer__credits">
          <span>Разработка сайта</span>
          <span>Твой стартап</span>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  position: relative;
  width: 100%;
  height: 575px;
  background: #496894;
  margin-top: 60px;
  overflow: hidden;
}
.footer__left, .footer__right {
  position: absolute;
  top: 0;
  width: 50%;
  height: 100%;
  background: #496894;
}
.footer__left {
  left: 0;
  border-radius: 0 250px 0 0;
}
.footer__right {
  right: 0;
  border-radius: 0 250px 0 0;
  transform: matrix(-1, 0, 0, 1, 0, 0);
}
.footer__content {
  position: relative;
  z-index: 1;
  max-width: 1820px;
  margin: 0 auto;
  padding: 100px 50px 0;
}
.footer__top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 100px;
}
.footer__text-left, .footer__text-right {
  font-family: 'Manrope', sans-serif;
  font-weight: 300;
  font-size: 36px;
  line-height: 100%;
  letter-spacing: -0.03em;
  color: #FFFFFF;
  max-width: 505px;
}
.footer__text-right {
  text-align: right;
}
.footer__button-center {
  background: #FFFFFF;
  border-radius: 50px;
  padding: 10px 30px;
  font-weight: 500;
  font-size: 16px;
  line-height: 100%;
  letter-spacing: -0.03em;
  color: #0B1B3A;
  cursor: pointer;
  transition: background 0.2s;
}
.footer__button-center:hover {
  background: #F0F0F0;
}
.footer__middle {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-top: 1px solid #B0CBE6;
  border-bottom: 1px solid #B0CBE6;
  padding: 20px 0;
  margin-bottom: 40px;
}
.footer__nav {
  display: flex;
  gap: 50px;
}
.footer__nav a {
  font-weight: 500;
  font-size: 16px;
  letter-spacing: -0.03em;
  color: #FFFFFF;
  transition: opacity 0.2s;
}
.footer__nav a:hover {
  opacity: 0.8;
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
  color: #FFFFFF;
}
.footer__logo {
  font-family: 'Riviera', sans-serif;
  font-size: 35px;
  line-height: 100%;
  color: #FFFFFF;
}
.footer__bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.footer__policy {
  font-weight: 500;
  font-size: 16px;
  letter-spacing: -0.03em;
  color: #FFFFFF;
}
.footer__credits {
  text-align: right;
  font-family: 'Inter', sans-serif;
}
.footer__credits span:first-child {
  font-weight: 500;
  font-size: 16px;
  color: #B0CBE6;
  display: block;
}
.footer__credits span:last-child {
  font-family: 'Riviera', sans-serif;
  font-size: 60px;
  line-height: 100%;
  letter-spacing: -0.03em;
  text-transform: uppercase;
  color: #FFFFFF;
}
</style>