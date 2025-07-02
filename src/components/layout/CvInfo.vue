<script setup lang="ts">
import MainBanner from "@/components/info/MainBanner.vue";
import TechStack from "@/components/info/TechStack.vue";
import MyAchievements from "@/components/info/MyAchievements.vue";
</script>

<template>
  <div class="cv-info">
    <MainBanner />
    <TechStack id="tech" />
    <MyAchievements id="achievements" />
  </div>
</template>

