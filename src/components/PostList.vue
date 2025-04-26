<template>
  <div class="post-list">
    <div v-for="post in posts" :key="post.id" class="post-card">
      <h2 class="post-title">{{ post.title }}</h2>
      <p class="post-excerpt">{{ post.excerpt }}</p>
      <div class="post-meta">
        <span class="post-date">{{ post.date }}</span>
        <Tags :tags="post.tags" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Tags from './Tags.vue'

interface Post {
  id: number
  title: string
  excerpt: string
  date: string
  tags: string[]
}

const posts = ref<Post[]>([
  {
    id: 1,
    title: 'Getting Started with Vue 3',
    excerpt: 'Learn the basics of Vue 3 and how to build your first application.',
    date: '2024-03-20',
    tags: ['Vue', 'JavaScript', 'Tutorial']
  },
  {
    id: 2,
    title: 'TypeScript for Vue Developers',
    excerpt: 'A comprehensive guide to using TypeScript with Vue 3.',
    date: '2024-03-21',
    tags: ['TypeScript', 'Vue', 'Development']
  }
])
</script>

<style scoped>
.post-list {
  @apply space-y-6;
}

.post-card {
  @apply p-6 bg-white rounded-lg shadow-md;
}

.post-title {
  @apply text-2xl font-bold text-gray-800 mb-2;
}

.post-excerpt {
  @apply text-gray-600 mb-4;
}

.post-meta {
  @apply flex items-center justify-between text-sm text-gray-500;
}

.post-date {
  @apply italic;
}
</style>
