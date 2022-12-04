<script setup>
const props = defineProps({
    isX: bool,
});
</script>
<template>
    <div>
        <img src="src/assets/cross.png" v-if="isX" />
        <img src="src/assets/circle.png" v-else />
    </div>
</template>
<style></style>