<template>
    <span class="wave-text">
      <span
        v-for="(char, i) in splitText"
        :key="i"
        class="char"
      >
        {{ char === ' ' ? '\u00A0' : char }}
      </span>
    </span>
  </template>
  
  <script>
  import gsap from 'gsap';
  
  export default {
    name: 'WaveText',
    props: {
      text: {
        type: String,
        required: true,
      },
    },
    computed: {
      splitText() {
        return this.text.split('');
      },
    },
    mounted() {
      gsap.to(this.$el.querySelectorAll('.char'), {
        y: -10,
        ease: 'sine.inOut',
        duration: 0.6,
        repeat: -1,
        yoyo: true,
        stagger: {
          each: 0.05,
          from: 'center',
        },
      });
    },
  };
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