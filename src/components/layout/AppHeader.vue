<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

const scrollPosition = ref(0);

function updateScroll() {
  scrollPosition.value = window.scrollY;
}

onMounted(() => {
  updateScroll(); // установить стартовое значение
  window.addEventListener("scroll", updateScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", updateScroll);
});
</script>


<template>
  <header class="header" :class="{ active: scrollPosition }">
    <div class="header__nav">
      <a class="header__nav-link" href="#tech">My Tech Stack</a>
      <a class="header__nav-link" href="#achievements">My Achievements</a>
    </div>
  </header>
</template>

<style scoped lang="scss">
.header {
  position: fixed;
  top: 0;
  width: 100%;
  gap: 20px;
  padding-top: 20px;
  padding-bottom: 20px;
  background-color: transparent;
  z-index: 12;
  will-change: transform;
  transition: 0.3s linear;

  @include center-items;

  &.active {
    background-color: #110f36;
  }

  &__nav {
    gap: 20px;

    @include center-items;
  }
}
</style>
