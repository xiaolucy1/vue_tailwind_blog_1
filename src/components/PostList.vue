<template>
  <div class="border border-gray-300 relative">
    <div v-for="post in posts" :key="post.title">
      <PostDetail :post="post" />
    </div>
    <div class="fixed bottom-0 left-0 w-full">
      <PreNextButtons />
    </div>
  </div>
</template>
<script setup lang="ts">
import { reactive } from 'vue';
import PostDetail from './PostDetail.vue';
import PreNextButtons from './PreNextButtons.vue';
const posts = reactive([
  {
    title: 'First Blog Post',
    description: 'This is the description for the first blog post.',
    date: '2023-10-26',
    tags: ['vue', 'tailwind', 'blog']
  },
  {
    title: 'Second Blog Post',
    description: 'This is the description for the second blog post.',
    date: '2023-10-27',
    tags: ['javascript', 'web development']
  },
  {
    title: 'Third Blog Post',
    description: 'This is the description for the third blog post.',
    date: '2023-10-28',
    tags: ['vue', 'components']
  }
])

</script>