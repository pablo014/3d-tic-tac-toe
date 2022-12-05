<script setup>
import {defineProps, ref} from 'vue';
const props = defineProps({
    isX: Boolean,
});
const isSelected = ref(false);
</script>
<template>
    <div class="h-20">
        <div v-if="isSelected">
            <img class="h-20" src="@/assets/cross.png" v-if="props.isX" />
            <img class="h-20" src="@/assets/circle.png" v-else />
        </div>
        <div @click="(isSelected = true)" v-else>
            <img class="h-20 opacity-0 hover:opacity-5" src="@/assets/cross.png" v-if="props.isX" />
            <img class="h-20 opacity-0 hover:opacity-5" src="@/assets/circle.png" v-else />
        </div>
    </div>
</template>
<style></style>