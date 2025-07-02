<script setup>
import rouletteWebp1x from "@/assets/images/games/roulette.webp";
import rouletteWebp2x from "@/assets/images/games/roulette@2x.webp";
import rouletteJpg1x from "@/assets/images/games/roulette.jpg";
import rouletteJpg2x from "@/assets/images/games/roulette@2x.jpg";
import aviatrixWebp1x from "@/assets/images/games/aviatrix.webp";
import aviatrixWebp2x from "@/assets/images/games/aviatrix@2x.webp";
import aviatrixJpg1x from "@/assets/images/games/aviatrix.jpg";
import aviatrixJpg2x from "@/assets/images/games/aviatrix@2x.jpg";
import banditWebp1x from "@/assets/images/games/bandit.webp";
import banditWebp2x from "@/assets/images/games/bandit@2x.webp";
import banditJpg1x from "@/assets/images/games/bandit.jpg";
import banditJpg2x from "@/assets/images/games/bandit@2x.jpg";
import chickenWebp1x from "@/assets/images/games/chicken.webp";
import chickenWebp2x from "@/assets/images/games/chicken@2x.webp";
import chickenJpg1x from "@/assets/images/games/chicken.jpg";
import chickenJpg2x from "@/assets/images/games/chicken@2x.jpg";

import { onMounted, nextTick } from "vue";
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

const images = [
  {
    alt: "Roulette",
    webp1x: rouletteWebp1x,
    webp2x: rouletteWebp2x,
    jpg1x: rouletteJpg1x,
    jpg2x: rouletteJpg2x,
    width: 450,
    height: 450,
  },
  {
    alt: "Aviatrix",
    webp1x: aviatrixWebp1x,
    webp2x: aviatrixWebp2x,
    jpg1x: aviatrixJpg1x,
    jpg2x: aviatrixJpg2x,
    width: 450,
    height: 300,
  },
  {
    alt: "Bandit",
    webp1x: banditWebp1x,
    webp2x: banditWebp2x,
    jpg1x: banditJpg1x,
    jpg2x: banditJpg2x,
    width: 450,
    height: 300,
  },
  {
    alt: "Chicken",
    webp1x: chickenWebp1x,
    webp2x: chickenWebp2x,
    jpg1x: chickenJpg1x,
    jpg2x: chickenJpg2x,
    width: 450,
    height: 300,
  },
  {
    alt: "Bandit",
    webp1x: banditWebp1x,
    webp2x: banditWebp2x,
    jpg1x: banditJpg1x,
    jpg2x: banditJpg2x,
    width: 450,
    height: 300,
  },
  {
    alt: "Chicken",
    webp1x: chickenWebp1x,
    webp2x: chickenWebp2x,
    jpg1x: chickenJpg1x,
    jpg2x: chickenJpg2x,
    width: 450,
    height: 300,
  },
  {
    alt: "Aviatrix",
    webp1x: aviatrixWebp1x,
    webp2x: aviatrixWebp2x,
    jpg1x: aviatrixJpg1x,
    jpg2x: aviatrixJpg2x,
    width: 450,
    height: 300,
  },
];

onMounted(async () => {
  await nextTick();

  const textEl = document.querySelector(".grid-area__heading");
  if (!textEl) return;

  const originalText = textEl.textContent || "";

  const words = originalText.split(" ");
  textEl.innerHTML = words.map((word) => `<span>${word} </span>`).join("");

  const spans = textEl.querySelectorAll("span");

  gsap.fromTo(
    spans,
    { opacity: 0, y: 20 },
    {
      scrollTrigger: {
        trigger: textEl,
        start: "top 80%",
        toggleActions: "play none none none",
      },
      opacity: 1,
      y: 0,
      stagger: 0.05,
      duration: 0.6,
      ease: "power2.out",
    }
  );

  gsap.to(textEl, {
    scrollTrigger: {
      trigger: textEl,
      start: "top 80%",
    },
    opacity: 1,
    duration: 0.2,
  });

  gsap.from(".grid-area__item", {
    scrollTrigger: {
      trigger: ".grid-area__list",
      start: "top 80%",
      toggleActions: "play none none reset",
    },
    opacity: 0,
    y: 50,
    stagger: 0.1,
    duration: 0.8,
    ease: "power2.out",
  });
});
</script>

<template>
  <div class="grid-area">
    <div class="container">
      <h3 class="grid-area__heading">
        I can create any kind of custom grid layout, no matter how complex. I
        also pay close attention to image optimization, ensuring fast loading
        times and responsive design across all devices.
      </h3>
      <div class="grid-area__list">
        <div
          class="grid-area__item"
          v-for="(img, index) in images"
          :key="index"
        >
          <picture>
            <source
              :srcset="`${img.webp1x} 1x, ${img.webp2x} 2x`"
              type="image/webp"
            />
            <img
              :src="img.jpg1x"
              :srcset="`${img.jpg1x} 1x, ${img.jpg2x} 2x`"
              :width="img.width"
              :height="img.height"
              loading="lazy"
              fetchpriority="low"
              decoding="async"
              :alt="img.alt"
            />
          </picture>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.grid-area {
  padding-bottom: 60px;

  &__heading {
    font-size: 20px;
    line-height: 1.6;
    max-width: 700px;
    margin: 60px auto;
    opacity: 0;
    color: $white;
    max-width: 100%;
    white-space: normal;

    span {
      display: inline-block;
      opacity: 0;
      transform: translateY(20px);
    }
  }

  &__list {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-auto-rows: 250px;
    gap: 16px;
    grid-template-areas:
      "roulette roulette aviatrix bandit chicken"
      "roulette roulette chicken2 aviatrix2 bandit2";

    @include media(sm) {
      grid-template-columns: 1fr;
      grid-template-areas: none;
      grid-auto-rows: auto;
    }
  }

  &__item {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: hidden;
    border-radius: 12px;

    &:nth-child(1) {
      grid-area: roulette;
    }

    &:nth-child(2) {
      grid-area: aviatrix;
    }

    &:nth-child(3) {
      grid-area: bandit;
    }

    &:nth-child(4) {
      grid-area: chicken;
    }

    &:nth-child(5) {
      grid-area: bandit2;
    }

    &:nth-child(6) {
      grid-area: chicken2;
    }

    &:nth-child(7) {
      grid-area: aviatrix2;
    }

    picture,
    img {
      width: 100%;
      height: 100%;
      display: block;
      object-fit: cover;
      object-position: center;
    }

    @include media(sm) {
      grid-area: auto !important;
    }
  }
}
</style>
