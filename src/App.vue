<template>
  <TBoard @calculate="onCalculate" />
</template>

<script>
import TBoard from './components/TBoard.vue'
import { ref, provide } from 'vue'

export default {
  name: 'App',
  components: {
    TBoard
  },
  setup() {
    const player = ref('x');
    const switchPlayer = (nextPlayer) => {
      player.value = nextPlayer;
    }
    provide('player', player);
    provide('switchPlayer', switchPlayer);
    const onCalculate = (winner) => {
      console.log(winner);
    };
    return {
      onCalculate,
    };
  }
}
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
