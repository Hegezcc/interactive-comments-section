<script setup>

import { computed } from 'vue';

import CommentList from './CommentList.vue';
import Votes from './Votes.vue';
import Actions from './Actions.vue';
import ProfilePicture from './ProfilePicture.vue';
import Timestamp from './Timestamp.vue';

const props = defineProps({
    comment: {
        type: Object,
        required: true
    }
})

const isOwn = computed(() => {
    return props.comment.username === 'juliusomo'
})

</script>
<template>
    <div class="comment">
        <ProfilePicture :picture="comment.user.image" :name="comment.user.username"></ProfilePicture>
        <h3>
            <span>{{ comment.user.username }}</span>
            <span v-if="isOwn" class="you">you</span>
        </h3>
        <Timestamp :time="comment.createdAt"></Timestamp>
        <div class="content">
            <a v-if="comment.replyingTo" href="#" class="tag">@{{ comment.replyingTo }}</a>
            {{ comment.content }}
        </div>
        <Votes :votes="comment.score"></Votes>
        <Actions :own="isOwn"></Actions>
    </div>
    <div class="replies">
        <CommentList :comments="comment.replies"></CommentList>
    </div>
</template>
<style scoped lang="scss">

</style>