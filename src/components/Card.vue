<script setup>
    import {defineProps } from 'vue';
    defineProps({
        bg: {
            type: String,
            default: 'bg-[#090a0a]'
        }
    })
</script>
<template>
    <div :class="`${bg} ring ring-green-900 ring-1  p-6 rounded-lg shadow-md`">
        <slot></slot>
    </div>
</template>