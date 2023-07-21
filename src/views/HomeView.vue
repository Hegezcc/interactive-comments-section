<script setup>
import CommentList from '../components/CommentList.vue';
import initialData from '@/data.json';

import moment from 'moment';
import { reactive } from 'vue';

// Parse times from relative times to timestamps
const now = moment();

function parseComment(comment) {
  // Take relative time e.g. "2 weeks ago", make it into parts and subtract from now
  comment.createdAt = now.subtract(...(comment.createdAt.split(' ago')[0].split(' '))).valueOf();
  if (comment.replies) {
    comment.replies.forEach(parseComment);
  }
}

initialData.comments.forEach(parseComment);

const data = reactive(initialData);

</script>

<template>
  <main>
    <CommentList :comments="data.comments" :current-user="data.currentUser" />
  </main>
</template>

<style scoped lang="scss">
@import '@/assets/base.scss';

main {
  max-width: $desktop-max;
  margin: 0 auto;
}
</style>