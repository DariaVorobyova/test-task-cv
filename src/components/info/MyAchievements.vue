<script setup lang="ts">
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
      <h2 class="my-achievements__title">My Achievements</h2>
      <div class="my-achievements__list">
        <div
          v-for="(item, id) in achievements"
          :key="id"
          class="my-achievements__item"
        >
          <p v-html="item" class="my-achievements__text"></p>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.my-achievements {
  padding: 0 0 100px;

  &__list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
  }

  &__item {
    padding: 20px;
    background: linear-gradient(90deg, #a03ab0, #007aff);
    border-radius: 16px;

    &:first-child {
      grid-column: 1 / 3;
    }
  }

  &__title {
    font-size: 48px;
    font-weight: 600;
    margin-bottom: 48px;

    background-image: linear-gradient(#aa85f4, #fff);
    color: transparent;
    background-clip: text;
  }

  &__text {
    font-size: 16px;
    font-weight: 600;

    @include text-shadow
  }
}
</style>
