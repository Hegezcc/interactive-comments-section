<script setup>
import CommentList from '../components/CommentList.vue';
import data from '@/data.json';
</script>

<template>
  <main>
    <CommentList :comments="data.comments" />
  </main>
</template>
