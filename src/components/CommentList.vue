<script setup>
import Comment from './Comment.vue';

defineProps({
    comments: {
        type: Array,
        required: true,
    }
})
</script>
<template>
    <div class="comment-list">
        <Comment v-for="comment of comments" :key="comment.id" :comment="comment"></Comment>
    </div>
</template>