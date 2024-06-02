<template>
    <div class="game-board">
      <div class="score">Score: {{ score }}</div>
      <div class="timer">Time Left: {{ timer }}</div>
      <div class="moles">
        <Mole v-for="n in 9" :key="n" @whacked="increaseScore" />
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref } from 'vue';
  import Mole from './Mole.vue';
  
  export default defineComponent({
    components: { Mole },
    setup() {
      const score = ref(0);
      const timer = ref(30); // 30 seconds timer
  
      const increaseScore = () => {
        score.value++;
      };
  
      // Timer logic
      setInterval(() => {
        if (timer.value > 0) {
          timer.value--;
        }
      }, 1000);
  
      return { score, timer, increaseScore };
    }
  });
  </script>
  
  <style scoped>
  .game-board {
    text-align: center;
  }
  .moles {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
  }
  </style>
  