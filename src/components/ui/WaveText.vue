<template>
  <span class="wave-text" ref="textRef">
    <span v-for="(char, i) in splitText" :key="i" class="char">
      {{ char === " " ? "\u00A0" : char }}
    </span>
  </span>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from "vue";
import gsap from "gsap";

interface Props {
  text: string;
}

const props = defineProps<Props>();

const textRef = ref<HTMLElement | null>(null);

const splitText = computed(() => props.text.split(""));

onMounted(() => {
  if (!textRef.value) return;

  const chars = textRef.value.querySelectorAll<HTMLElement>(".char");

  gsap.to(chars, {
    y: -10,
    ease: "sine.inOut",
    duration: 0.6,
    repeat: -1,
    yoyo: true,
    stagger: {
      each: 0.05,
      from: "center",
    },
  });
});
</script>

<style scoped lang="scss">
.wave-text {
  display: inline-block;
}

.char {
  display: inline-block;
  background-image: linear-gradient($secondary, #ffffff);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  will-change: transform;
}
</style>
