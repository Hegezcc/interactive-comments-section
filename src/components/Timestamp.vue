<script setup>
defineProps({
    time: {
        type: String,
        required: true,
    }
})
</script>

<template>
    <div class="timestamp">
        {{ new Date(time).toLocaleString() }}
    </div>
</template>