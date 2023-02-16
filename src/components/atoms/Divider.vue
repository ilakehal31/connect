<script setup lang="ts">

defineProps<{ text : string}>()

</script>

<template>
    <div class="divider">
        {{ text }}
    </div>
</template>

<style scoped>
    .divider {
        display: flex;
        align-items: center;
        text-align: center;
    }

    .divider::after,.divider::before {
        content: "";
        border: 0.5px solid rgb(162, 162, 162);
        flex: 1;
    }

    .divider:not(:empty)::before {
        margin-right: 0.25em;
    }

    .divider:not(:empty)::after {
        margin-left: 0.25em;
    }
</style>