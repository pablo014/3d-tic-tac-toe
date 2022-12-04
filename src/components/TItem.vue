<script setup>
import {defineProps} from 'vue';
const props = defineProps({
    isX: Boolean,
});
</script>
<template>
    <div>
        <img src="@/assets/cross.png" v-if="props.isX" />
        <img src="@/assets/circle.png" v-else />
    </div>
</template>
<style></style>