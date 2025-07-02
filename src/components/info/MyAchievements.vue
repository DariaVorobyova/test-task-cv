<script setup lang="ts">
import WaveText from "@/components/ui/WaveText.vue";
import TextAppear from "@/components/ui/TextAppear.vue";

const achievements = [
  `Advabet: August 2020 - September 2022 <br/> Mind Studios: September 2022 - July 2025`,
  "With a strong background in modern web development and a particular focus on the Vue.js ecosystem, I’m excited about the opportunity to bring clean, scalable, and maintainable code to your team.",
  "Over the past 4+ years, I have built and maintained a range of Vue-based applications using technologies like Vue, Nuxt, Pinia, Vuex, Vue Router, and Vite, as well as  SCSS, and REST for backend integration.",
  "Developing web applications for outsource projects in gaming industry using Vue.js. and Nuxt.js",
  "Creating landing pages and responsive layouts compatible with multiple browsers based on design mockups",
  "Learning new front-end technologies and approaches to development",
  "Optimizing  app's user interface, prioritizing performance by reducing unnecessary code",
  "Working closely with back-end developers to ensure of data handling",
  "Translating business requirements into code",
  "Following best practices in component design, state management, and performance optimization",
  "Prioritize accessibility and responsiveness in every UI I create",
];
</script>

<template>
  <div class="my-achievements">
    <div class="container">
      <h2 class="my-achievements__title">
        <WaveText text="My Achievements" />
      </h2>
      <div class="my-achievements__list">
        <TextAppear
          v-for="(item, id) in achievements"
          :key="id"
          direction="x"
          :distance="100"
          :delay="id * 0.05"
          class="my-achievements__item"
        >
          <p class="my-achievements__text" v-html="item"></p>
        </TextAppear>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.my-achievements {
  padding-bottom: 60px;

  &__title {
    margin-bottom: 48px;
    @include text-shadow;;
  }

  &__list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;

    @include media(sm) {
      grid-template-columns: 1fr;
    }
  }

  &__item {
    position: relative;
    padding: 20px;
    border-radius: 16px;
    background: linear-gradient($primary, $primary) padding-box,
      linear-gradient(90deg, #a03ab0, #007aff) border-box;
    border: 5px solid transparent;

    transition: transform 0.3s ease, opacity 0.3s ease;

    &:first-child {
      grid-column: span 2;
    }

    @include media(sm) {
      grid-column: auto !important;
    }
  }

  &__text {
    font-size: 16px;
    font-weight: 600;
    @include text-shadow;
  }
}
</style>
