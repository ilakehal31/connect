<script setup lang="ts">

defineProps<{ text: string}>()

</script>

<template>
    <a href="#"> {{text}} </a>
</template>

<style scoped>
    a {
        border-bottom: 1px solid black;
    }
</style>