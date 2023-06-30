<script setup>
defineProps({
    own: {
        type: Boolean,
        required: false,
        default: false
    }
})
</script>
<template>
    <div class="actions">
        <button v-if="own">Edit</button>
        <button v-if="own">Delete</button>
        <button v-if="!own">Reply</button>
    </div>
</template>