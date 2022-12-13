<template>
  <TBoard :active-index="active">
    <template #item="slotProps">
      <div class="relative " :class="slotProps.pRecord.x.includes(slotProps.index) ? 'bg-red-400' : slotProps.pRecord.o.includes(slotProps.index) ? 'bg-blue-400' : ''">
        <div v-if="!slotProps.isActive" class="w-full h-full bg-gray-400 opacity-40 absolute" />
        <TBoard :isDisabled="!slotProps.isActive" @click="(index) => {
          if (slotProps.isActive) {
            active = index;
          }
        }" @calculate="(winner) => {
          if(winner != '') {
            slotProps.calculateWinner(slotProps.index)
          }
        }"/>
      </div>
    </template>
  </TBoard>
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
    const active = ref(5);
    const switchPlayer = (nextPlayer) => {
      player.value = nextPlayer;
    }
    provide('player', player);
    provide('switchPlayer', switchPlayer);
    return {
      active,
    }
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
