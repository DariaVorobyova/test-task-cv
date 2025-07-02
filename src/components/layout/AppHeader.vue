<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

const scrollPosition = ref(0);

function updateScroll() {
  scrollPosition.value = window.scrollY;
}

onMounted(() => {
  updateScroll(); 
  window.addEventListener("scroll", updateScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", updateScroll);
});
</script>


<template>
  <header class="site-header" :class="{ 'site-header--active': scrollPosition }">
    <div class="site-header__nav">
      <a class="site-header__nav-link" href="#tech">My Tech Stack</a>
      <a class="site-header__nav-link" href="#achievements">My Achievements</a>
    </div>
  </header>
</template>

<style scoped lang="scss">
.site-header {
  position: fixed;
  top: 0;
  display: flex;
  width: 100%;
  gap: 20px;
  padding-top: 20px;
  padding-bottom: 20px;
  background-color: transparent;
  z-index: 12;
  will-change: transform;
  transition: 0.3s linear;

  @include center-items;

  &--active {
    background-color: #110f36;
  }

  &__nav {
    display: flex;
    gap: 20px;

    @include center-items;
  }
}
</style>
