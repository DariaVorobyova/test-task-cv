<script setup lang="ts">
import CometOrange from "@/components/ui/CometOrange.vue";
import CometBlue from "@/components/ui/CometBlue.vue";

import WaveText from "@/components/ui/WaveText.vue";
import TextAppear from "@/components/ui/TextAppear.vue";

const technologies = [
  "Vue",
  "Nuxt",
  "JavaScript",
  "Vuex",
  "Pinia",
  "Vuetify",
  "Element+",
  "Tailwind",
  "Gsap",
  "Lodash",
  "Vite",
  "Lint",
  "HTML",
  "CSS",
  "Flex",
  "Grid",
];
</script>

<template>
  <div class="tech-stack">
    <div class="container">
      <h2 class="tech-stack__title">
        <WaveText text="My Tech Stack" />
      </h2>
      <div class="tech-stack__list">
        <TextAppear
          v-for="(item, id) in technologies"
          :key="id"
          direction="x"
          :distance="-100"
          :delay="id * 0.05"
          class="tech-stack__item"
        >
          <p class="tech-stack__text">{{ item }}</p>
        </TextAppear>
      </div>
      <CometOrange class="tech-stack__comet tech-stack__comet--orange" />
      <CometBlue class="tech-stack__comet tech-stack__comet--blue" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.tech-stack {
  padding: 20px 0 320px;
  position: relative;

  &__title {
    margin-bottom: 48px;
    @include text-shadow;
  }

  &__list {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;

    @include center-items;
  }

  &__item {
    display: flex;
    width: calc(25% - 72px);
    min-height: 60px;
    padding: 16px;

    background-image: linear-gradient($secondary, $secondary),
      linear-gradient($secondary, $secondary),
      linear-gradient($secondary, $secondary),
      linear-gradient($secondary, $secondary),
      linear-gradient(
        to top left,
        transparent calc(50% - 3px),
        $secondary calc(50% - 3px),
        $secondary calc(50% + 1px),
        transparent calc(50% + 1px)
      ),
      linear-gradient(
        114deg,
        rgba(255, 0, 77, 0.2) 0%,
        rgba(255, 0, 77, 0) 100%
      );
    background-size: 3px 100%, 3px 100%, 100% 3px, 100% 4px, 20px 20px,
      100% 100%, contain;
    background-position: 0 0, 100% -16px, 0 0%, -16px calc(100% + 1px),
      100% 100%, 100% 100%, left top;
    background-repeat: no-repeat;

    @include center-items;

    @include media(sm) {
      width: 100%;
    }
  }

  &__text {
    font-size: 30px;
    font-weight: 600;
    color: transparent;
    -webkit-text-stroke: 1px white;
  }

  &__comet {
    position: absolute;
    z-index: 2;

    &--blue {
      right: 0;
      left: 0;
      margin: auto;
      animation: tech-stack-blue-planet 2s ease-in-out infinite alternate;
    }

    &--orange {
      right: 20px;
      animation: tech-stack-orange-planet 2s ease-in-out infinite alternate;

      @include media(sm) {
        width: 150px;
      }
    }
  }

  @keyframes tech-stack-blue-planet {
    from {
      transform: translate(-20%, 50px);
    }
    to {
      transform: translate(-40%, 200px);
    }
  }

  @keyframes tech-stack-orange-planet {
    from {
      transform: translate(0%, 0px);
    }
    to {
      transform: translate(-100px, 60px);
    }
  }
}
</style>
