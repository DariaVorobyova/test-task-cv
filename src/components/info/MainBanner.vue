<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay } from "swiper/modules";
import "swiper/css";

import banner1 from "@/assets/images/banners/banner-1.png";
import banner2 from "@/assets/images/banners/banner-2.png";
import banner3 from "@/assets/images/banners/banner-3.png";

const texts = [
  "Frontend Developer with 4+ years of experience in developing web applications across various sectors using Vue.js and Nuxt.js.",
  "Transforming design mockups into responsive, high-performance user interfaces.",
  "Passionate about creating innovative web experiences. Eager for new challenges and ready to develop my skills along with the company.",
];

const banners = [banner1, banner2, banner3];
</script>

<template>
  <div class="main-banner">
    <ClientOnly>
      <swiper
        :modules="[Autoplay]"
        :slides-per-view="1"
        :loop="true"
        :autoplay="{ delay: 3000 }"
        class="main-banner__swiper"
      >
        <swiper-slide v-for="(banner, index) in banners" :key="index">
          <div class="slide-content">
            <div class="slide-text">
              <h2>Daria Vorobiova</h2>
              <p>{{ texts[index] }}</p>
            </div>
            <div class="slide-image">
              <img :src="banner" alt="Banner" />
            </div>
          </div>
        </swiper-slide>
      </swiper>
    </ClientOnly>
  </div>
</template>

<style lang="scss">
.main-banner {
  padding: 60px 0;
  background-image: url("@/assets/images/background/banner-bg.jpg");

  @include retina {
    background-image: url("@/assets/images/background/banner-bg.webp");
  }

  &__swiper {
    width: 100%;
    height: 400px;
    position: relative;
    overflow: hidden;

    .swiper-slide {
      display: flex;
     @include center-items
    }

    .slide-content {
      display: flex;
      width: 100%;
      height: 100%;
    }

    .slide-image {
      width: 60%;
      height: 100%;
    }

    .slide-text {
      flex-direction: column;
      width: 40%;
      padding: 24px;
      text-align: center;

      @include text-shadow;
      @include center-items;
    }

    .swiper-slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
}
</style>
