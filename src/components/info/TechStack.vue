<script setup lang="ts">
import CometOrange from "@/components/ui/CometOrange.vue";
import CometBlue from "@/components/ui/CometBlue.vue";

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
      <h2 class="tech-stack__title">My Tech Stack</h2>
      <div class="tech-stack__list">
        <div
          v-for="(item, id) in technologies"
          :key="id"
          class="tech-stack__item"
        >
          <p class="tech-stack__text">
            {{ item }}
          </p>
        </div>
      </div>
      <CometOrange class="cometOrange" />
      <CometBlue class="cometBlue" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.tech-stack {
  padding: 20px 0 320px;

  &__title {
    font-size: 48px;
    font-weight: 600;
    margin-bottom: 48px;

    background-image: linear-gradient($secondary, #fff);
    color: transparent;
    background-clip: text;
  }

  &__list {
    flex-wrap: wrap;
    gap: 20px;

    @include center-items;
  }

  &__item {
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
  }

  &__text {
    font-size: 30px;
    font-weight: 600;

    @include text-shadow;
  }

  .cometBlue {
    position: absolute;
    right: 0;
    left: 0;
    margin: auto;
    animation: blue-planet 2s ease-in-out;
    animation-iteration-count: infinite;
    animation-direction: alternate;
  }
  @keyframes blue-planet {
    from {
      transform: translate(-20%, 50px);
    }
    to {
      transform: translate(-40%, 200px);
    }
  }

  .cometOrange {
    position: absolute;
    right: 20px;
    animation: orange-planet 2s 0ms ease-in-out;
    animation-iteration-count: infinite;
    animation-direction: alternate;
    z-index: 2;
  }

  @keyframes orange-planet {
    from {
      transform: translate(0%, 0px);
    }

    to {
      transform: translate(-100px, 60px);
    }
  }
}
</style>
