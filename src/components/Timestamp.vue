<script setup>
import moment from 'moment';

defineProps({
    time: {
        type: Number,
        required: true,
    }
})
</script>

<template>
    <div class="timestamp">
        {{ moment(time).fromNow() }}
    </div>
</template>