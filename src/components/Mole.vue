<template>
    <div class="mole" @click="whackMole" :class="{ visible: isVisible }">
      🐹
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref, onMounted } from 'vue';
  
  export default defineComponent({
    setup(props, { emit }) {
      const isVisible = ref(false);
  
      const whackMole = () => {
        if (isVisible.value) {
          isVisible.value = false;
          emit('whacked');
        }
      };
  
      const showMole = () => {
        isVisible.value = true;
        setTimeout(() => {
          isVisible.value = false;
        }, 1000); // mole is visible for 1 second
      };
  
      // Show moles at random intervals
      onMounted(() => {
        setInterval(() => {
          if (!isVisible.value) {
            showMole();
          }
        }, Math.random() * 2000 + 1000); // between 1-3 seconds
      });
  
      return { isVisible, whackMole };
    }
  });
  </script>
  
  <style scoped>
  .mole {
    width: 100px;
    height: 100px;
    background: brown;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2em;
    border-radius: 50%;
    opacity: 0;
    transition: opacity 0.3s;
  }
  
  .mole.visible {
    opacity: 1;
  }
  </style>
  