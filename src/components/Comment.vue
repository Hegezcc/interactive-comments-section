<script setup>

import { BaseTransitionPropsValidators, computed } from 'vue';

import CommentList from './CommentList.vue';
import Votes from './Votes.vue';
import Actions from './Actions.vue';
import ProfilePicture from './ProfilePicture.vue';
import Timestamp from './Timestamp.vue';

const props = defineProps({
    comment: {
        type: Object,
        required: true
    },
    currentUser: {
        type: Object,
        required: true
    },
})

const isOwn = computed(() => {
    return props.comment.user.username === props.currentUser.username;
})

function changeScore(amount) {
    props.comment.score += amount;
}

</script>
<template>
    <div class="comment">
        <ProfilePicture class="picture" :picture="comment.user.image" :name="comment.user.username"></ProfilePicture>
        <h3 class="name">
            <span>{{ comment.user.username }}</span>
            <span v-if="isOwn" class="you">you</span>
        </h3>
        <Timestamp class="timestamp" :time="comment.createdAt"></Timestamp>
        <div class="content">
            <a v-if="comment.replyingTo" href="#" class="tag">@{{ comment.replyingTo }}</a>
            {{ comment.content }}
        </div>
        <Votes class="votes" :score="comment.score" @change="changeScore"></Votes>
        <Actions clsas="actions" :own="isOwn"></Actions>
    </div>
    <div class="replies" v-if="comment.replies">
        <CommentList 
            :comments="comment.replies"
            :current-user="currentUser"
        ></CommentList>
    </div>
</template>
<style scoped lang="scss">
@import '@/assets/base.scss';

.comment {
    display: grid;
    grid-template-areas: 
        "picture name timestamp"
        "content content content"
        "votes actions actions"
        "replies replies replies";

    grid-template-columns: 2rem auto 1fr;
    grid-gap: 1rem;
}

.content {
    grid-area: content;
}

.picture {
    grid-area: picture;
}

.timestamp {
    grid-area: timestamp;
}

.votes {
    grid-area: votes;
}

.actions {
    grid-area: actions;
}

.name {
    margin: 0;
    font-size: 1rem;
    grid-area: name;

    .you {
        background: $moderate-blue;
        color: $white;
        margin-left: 0.25rem;
        border-radius: 0.125rem;
        padding: 0.125rem 0.5rem;
    }
}

.replies {
    position: relative;
    grid-area: replies;
    margin-left: 2rem;

    &::before {
        content: "";
        position: absolute;
        top: 0;
        left: -2rem;
        bottom: 0;
        width: 1px;
        background: $grayish-blue;
    }
}
</style>