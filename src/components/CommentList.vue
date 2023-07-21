<script setup>
import Comment from './Comment.vue';

defineProps({
    comments: {
        type: Array,
        required: true,
    },
    currentUser: {
        type: Object,
        required: true
    },
})
</script>
<template>
    <div class="comment-list">
        <Comment v-for="comment of comments" 
            :key="comment.id" 
            :comment="comment"
            :current-user="currentUser"
        ></Comment>
    </div>
</template>