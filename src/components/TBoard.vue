<script setup>
import TItem from './TItem.vue';
import {ref, defineEmits, inject} from 'vue';
const player = inject('player');
const emit = defineEmits(['winner'])
const pRecord = ref({
    'x': [],
    'o': [],
});
const winningLines = [
    [1,2,3],
    [4,5,6],
    [7,8,9],
    [1,4,7],
    [2,5,6],
    [3,6,9],
    [1,5,9],
    [3,5,7],
];
const calculateWinner = (index) => {
    console.log(pRecord.value[player.value], index)
    pRecord.value[player.value].push(index);
    const playerR = pRecord.value[player.value];
    var winner = '';
    //Go through all the winnning lines
    winningLines.forEach((i) => {
        //check if player has numbers that match up those lines
        if(playerR.includes(i[0]) && playerR.includes(i[1]) && playerR.includes(i[2])){
            winner = player.value;
        }
    })
    emit('calculate', winner);
}
</script>
<template>
    <div class="flex flex-wrap">
        <div class="w-1/3 border-2 border-black flex items-center justify-center" v-for="index in 9" :key="index">
            <slot name="item">
                <TItem @click="calculateWinner(index)"/>
            </slot>
        </div>
    </div>
</template>
<style></style>