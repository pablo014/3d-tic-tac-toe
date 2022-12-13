<script setup>
import TItem from './TItem.vue';
import { winningLines } from '@/constants.ts';
import {ref, defineEmits, inject, defineProps} from 'vue';
const player = inject('player');
const winner = ref('');
const emit = defineEmits(['calculate', 'click']);
const props = defineProps({
    activeIndex: Number,
    isDisabled: Boolean
});
const pRecord = ref({
    'x': [],
    'o': [],
});
const calculateWinner = (index) => {
    emit('click', index);
    //only if winner has not been determined
    if (winner.value == '' && !props.isDisabled) {
        pRecord.value[player.value].push(index);
        const playerR = pRecord.value[player.value];
        //Go through all the winnning lines
        winningLines.forEach((i) => {
        //check if player has numbers that match up those lines
        if(playerR.includes(i[0]) && playerR.includes(i[1]) && playerR.includes(i[2])){
            winner.value = player.value;
        }
    })
    emit('calculate', winner.value, index);
    }
}
</script>
<template>
    <div class="flex flex-wrap">
        <div class="w-1/3 border-2 border-black flex items-center justify-center" v-for="index in 9" :key="index">
            <slot name="item" :index="index" :calculateWinner="calculateWinner" :pRecord="pRecord" :isActive="props.activeIndex === index">
                <TItem :isDisabled="props.isDisabled" @click="() => calculateWinner(index)" />
            </slot>
        </div>
    </div>
</template>
<style></style>