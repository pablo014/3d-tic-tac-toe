<script setup>
import {ref, inject} from 'vue';
//who's turn is it injected from app
const player = inject('player');
const switchPlayer = inject('switchPlayer');
const isSelected = ref(false);
//The local value of that will set which player placed
const value = ref();

const setValue = () => {
    isSelected.value = true;
    value.value = player.value;
    switchPlayer(value.value === 'x' ? 'o' : 'x');
}
</script>
<template>
    <div class="h-20">
        <div v-if="isSelected">
            <img class="h-20" src="@/assets/cross.png" v-if="value === 'x'" />
            <img class="h-20" src="@/assets/circle.png" v-else />
        </div>
        <div @click="setValue()" v-else>
            <img class="h-20 opacity-0 hover:opacity-5" src="@/assets/cross.png" v-if="player === 'x'" />
            <img class="h-20 opacity-0 hover:opacity-5" src="@/assets/circle.png" v-else />
        </div>
    </div>
</template>
<style></style>