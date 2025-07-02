<script setup lang="ts">
import { ref, onMounted } from 'vue';

const props = defineProps<{ text: string }>();
const letters = ref<string[]>([]);

onMounted(() => {
  letters.value = props.text.split('');
});
</script>

<template>
  <span class="bouncing-text">
    <span
      v-for="(char, index) in letters"
      :key="index"
      class="bouncing-text__letter"
      :style="{ animationDelay: `${index * 0.05}s` }"
    >
      {{ char }}
    </span>
  </span>
</template>

<style scoped lang="scss">
.bouncing-text {
  display: inline-block;
  white-space: nowrap;
  font-weight: 800;
  margin-bottom: 8px;

  &__letter {
    display: inline-block;
    animation: bounce 1s ease-in-out infinite;
  }
}

@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}
</style>