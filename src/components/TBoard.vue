<script setup>
import TItem from './TItem.vue';
</script>
<template>
    <div class="flex flex-wrap">
        <div class="w-1/3 border-2 border-black flex items-center justify-center" v-for="index in 9" :key="index">
            <TItem :isX="false" />
        </div>
    </div>
</template>
<style></style>