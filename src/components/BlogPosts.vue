<template>
  <div class="flex flex-row border p-4">
    <div class="w-3/4">
      <PostList />
    </div>
    <div class="w-1/4">
      <Tags />
    </div>
  </div>
</template>

<script setup lang="ts">
import PostList from './PostList.vue';
import Tags from './Tags.vue';
</script>