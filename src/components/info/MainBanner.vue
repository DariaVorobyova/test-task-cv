<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay } from "swiper/modules";
import "swiper/css";

const texts = [
  "Daria Vorobiova. Frontend Developer with 4+ years of experience in developing web applications across various sectors using Vue.js and Nuxt.js. Transforming design mockups into responsive, high-performance user interfaces. Passionate about creating innovative web experiences. Eager for new challenges and ready to develop my skills along with the company.",
  "Daria Vorobiova. Frontend Developer with 4+ years of experience in developing web applications across various sectors using Vue.js and Nuxt.js. Transforming design mockups into responsive, high-performance user interfaces. Passionate about creating innovative web experiences. Eager for new challenges and ready to develop my skills along with the company.",
  "Daria Vorobiova. Frontend Developer with 4+ years of experience in developing web applications across various sectors using Vue.js and Nuxt.js. Transforming design mockups into responsive, high-performance user interfaces. Passionate about creating innovative web experiences. Eager for new challenges and ready to develop my skills along with the company.",
];

import banner1 from "@/assets/images/banners/banner-1.png";
import banner2 from "@/assets/images/banners/banner-2.png";
import banner3 from "@/assets/images/banners/banner-3.png";

const banners = [
  {
    webp: new URL("@/assets/images/banners/banner-1.webp", import.meta.url)
      .href,
    png: banner1,
  },
  {
    webp: new URL("@/assets/images/banners/banner-2.webp", import.meta.url)
      .href,
    png: banner2,
  },
  {
    webp: new URL("@/assets/images/banners/banner-3.webp", import.meta.url)
      .href,
    png: banner3,
  },
];
</script>

<template>
  <div class="main-banner">
    <div class="container">
      <ClientOnly>
        <swiper
          :modules="[Autoplay]"
          :slides-per-view="1"
          :loop="true"
          :autoplay="{ delay: 3000 }"
          class="main-banner__swiper"
        >
          <swiper-slide
            v-for="(banner, index) in banners"
            :key="index"
            class="main-banner__slide"
          >
            <div class="main-banner__content">
              <div class="main-banner__text">
                <div class="main-banner__paragraph-wrap">
                  <img
                    src="@/assets/images/photo.jpg"
                    alt="Daria Avatar"
                    class="main-banner__inline-image"
                  />
                  <p>{{ texts[index] }}</p>
                </div>
                <a
                  class="main-banner__btn btn"
                  href="mailto:dasha090498@gmail.com"
                  >Contact Me</a
                >
              </div>
              <div class="main-banner__image">
                <picture>
                  <source :srcset="banner.webp" type="image/webp" />
                  <img :src="banner.png" alt="Banner" />
                </picture>
              </div>
            </div>
          </swiper-slide>
        </swiper>
      </ClientOnly>
    </div>
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

    @include media(sm) {
      height: max-content;
    }
  }

  &__slide {
    display: flex;
    @include center-items;

    @include media(sm) {
      overflow: hidden;
    }
  }

  &__content {
    display: flex;
    width: 100%;
    height: 100%;

    @include media(sm) {
      flex-direction: column;
    }
  }

  &__text {
    display: flex;
    width: 40%;
    padding: 24px;
    text-align: center;
    flex-direction: column;
    @include center-items;
    @include text-shadow;

    @include media(sm) {
      width: 100%;
      padding: 0;
    }
  }

  &__paragraph-wrap {
    position: relative;
    text-align: left;

    p {
      margin: 0 0 40px;
      font-size: 20px;
    }
  }

  &__btn {
    @include media(sm) {
      margin-bottom: 20px;
    }
  }

  &__inline-image {
    float: left;
    width: 80px;
    height: 80px;
    object-fit: cover;
    border-radius: 50%;
    margin: 10px 16px 8px 0;
  }

  &__image {
    width: 60%;
    height: 100%;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    @include media(sm) {
      width: 100%;
    }
  }
}
</style>
