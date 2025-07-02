<template>
    <div ref="elRef" class="text-appear">
      <slot />
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted, nextTick } from "vue";
  import gsap from "gsap";
  import ScrollTrigger from "gsap/ScrollTrigger";
  
  gsap.registerPlugin(ScrollTrigger);
  
  interface Props {
    direction?: "x" | "y";
    distance?: number;
    delay?: number;
    triggerStart?: string;
  }
  
  const props = withDefaults(defineProps<Props>(), {
    direction: "x",
    distance: 100,
    delay: 0,
    triggerStart: "top 85%",
  });
  
  const elRef = ref<HTMLElement | null>(null);
  
  onMounted(async () => {
    await nextTick();
  
    if (!elRef.value) return;
  
    const fromVars: Record<string, any> = {
      opacity: 0,
      [props.direction]: props.distance,
    };
  
    const toVars: Record<string, any> = {
      opacity: 1,
      [props.direction]: 0,
      duration: 0.8,
      ease: "power2.out",
      delay: props.delay,
      scrollTrigger: {
        trigger: elRef.value,
        start: props.triggerStart,
        toggleActions: "play none none none",
      },
    };
  
    gsap.fromTo(elRef.value, fromVars, toVars);
  });
  </script>
  
  <style scoped>
  .text-appear {
    will-change: transform, opacity;
  }
  </style>