<script setup>
import Dashboard from "@/components/Dashboard.vue";
import Sidebar from "@/components/Sidebar.vue";

import figma from "@/assets/img/Figma.svg";
</script>

<template>
  <div class="promo">
    <div class="container container__big">
      <!-- <div class="promo__title">Free Admin <br />Dashboard Template</div> -->
      <div class="promo__content">
        <div class="promo__title">Free Admin <br />Dashboard Template</div>
        <Dashboard class="promo__dash1" />
        <Sidebar class="promo__dash2" />
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.promo .container {
  position: relative;
}
.promo {
  background: url(../assets/img/Cover.png) no-repeat center center;
  background-size: cover;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  &__content {
    display: flex;
    height: 100vh;
    width: 100%;
  }
  &__title {
    font-weight: bold;
    font-size: clamp(25px, 3vw, 55px);
    color: var(--color-white);
    margin-top: 50px;
    line-height: 64px;
  }
  &__dash1 {
    position: absolute;
    bottom: 0;
    right: 95px;
    z-index: 100;
  }
  &__dash2 {
    position: absolute;
    bottom: -60px;
    z-index: 1;
  }
}
.promo .sidebar {
  border-top-left-radius: 24px;
}
.promo .dashboard__content {
  border-top-right-radius: 24px;
}

@media (max-width: 1920px) {
  .container {
    padding: 0 15px;
  }
  .promo__dash1 {
    bottom: -90px;
  }
  .promo__dash2 {
    left: 15px;
    bottom: -120px;
  }
}
@media (max-width: 1600px) {
  .container {
    padding: 0 15px;
  }
  .promo__dash1 {
    bottom: -220px;
  }
  .promo__dash2 {
    left: 15px;
    bottom: -270px;
  }
}

@media (max-width: 1440px) {
  .promo__dash1 {
    bottom: -320px;
  }
  .promo__dash2 {
    left: 15px;
    bottom: -370px;
  }
}
@media (max-width: 1300px) {
  .promo__dash1 {
    bottom: -350px;
  }
  .promo__title {
    font-size: 35px;
    margin-top: 25px;
    line-height: 45px;
  }
  .promo__dash2 {
    display: none;
  }
}
@media (max-width: 1024px) {
  .promo__dash1 {
    bottom: -180px;
    right: auto;
  }
  .sidebar {
    padding: 38px 15px !important;
  }
}
@media (max-width: 768px) {
  .promo__title {
    font-size: 25px;
    line-height: 30px;
  }
  .promo__dash1 {
    bottom: -100px;
    right: auto;
  }
  .sidebar__logo {
    font-size: 16px !important;
    line-height: 18px !important;
    img {
      width: 20px;
      height: 20px;
    }
  }
}
</style>
