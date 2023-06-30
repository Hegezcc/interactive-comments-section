<script setup>
defineProps({
    score: {
        type: Number,
        required: true,
    }
})
</script>
<template>
    <div class="votes">
        <button>+</button>
        <span>{{ score }}</span>
        <button>-</button>
    </div>
</template>