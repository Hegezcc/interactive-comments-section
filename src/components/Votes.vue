<script setup>
const props = defineProps({
    score: {
        type: Number,
        required: true,
    }
});

defineEmits(['change']);

</script>
<template>
    <div class="votes">
        <button @click="$emit('change', 1)">+</button>
        <span>{{ score }}</span>
        <button @click="$emit('change', -1)">-</button>
    </div>
</template>