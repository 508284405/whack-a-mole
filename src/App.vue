<template>
  <div id="app">
    <GameBoard />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import GameBoard from './components/GameBoard.vue';

export default defineComponent({
  components: {
    GameBoard
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
