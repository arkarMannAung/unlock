<script setup>
    let props = defineProps({
        path:{
            type: String,
            required: true
        },
        size:{
            type: String,
            required: false,
            default: "24"
        }
    });
</script>
<template>
    <svg :width="size" :height="size" viewBox="0 0 24 24" class="inline-block" xmlns="http://www.w3.org/2000/svg">
        <path fill="currentColor" :d="path"></path>
    </svg>
</template>