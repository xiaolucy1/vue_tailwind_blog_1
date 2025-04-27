<template>
  <div class="border border-gray-300 p-4 mb-4">
    <h3 class="text-lg font-bold">{{ post.title }}</h3>
    <p class="text-gray-700 mt-2">{{ post.description }}</p>
    <div class="text-sm text-gray-500 mt-2">{{ post.date }}</div>
    <div class="mt-2">
      <span v-for="tag in post.tags" :key="tag" class="inline-block bg-blue-200 rounded-full px-3 py-1 text-sm font-semibold text-blue-800 mr-2">
        {{ tag }}
      </span>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps<{ post: { title: string; description: string; date: string; tags: string[] } }>();
</script>