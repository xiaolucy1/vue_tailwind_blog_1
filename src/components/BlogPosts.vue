<template>
  <div class="blog-posts">
    <div class="header">
      <h1 class="title">Blog Posts</h1>
      <div class="filters">
        <input
          v-model="searchQuery"
          type="text"
          placeholder="Search posts..."
          class="search-input"
        />
        <select v-model="selectedTag" class="tag-filter">
          <option value="">All Tags</option>
          <option v-for="tag in allTags" :key="tag" :value="tag">
            {{ tag }}
          </option>
        </select>
      </div>
    </div>
    <PostList :posts="filteredPosts" />
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import PostList from './PostList.vue'

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
  },
  {
    id: 3,
    title: 'Building a Blog with Vue and Tailwind',
    excerpt: 'Step-by-step guide to creating a modern blog using Vue 3 and Tailwind CSS.',
    date: '2024-03-22',
    tags: ['Vue', 'Tailwind', 'Tutorial']
  }
])

const searchQuery = ref('')
const selectedTag = ref('')

const allTags = computed(() => {
  const tags = new Set<string>()
  posts.value.forEach(post => {
    post.tags.forEach(tag => tags.add(tag))
  })
  return Array.from(tags)
})

const filteredPosts = computed(() => {
  return posts.value.filter(post => {
    const matchesSearch = post.title.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
                         post.excerpt.toLowerCase().includes(searchQuery.value.toLowerCase())
    const matchesTag = !selectedTag.value || post.tags.includes(selectedTag.value)
    return matchesSearch && matchesTag
  })
})
</script>

<style scoped>
.blog-posts {
  @apply max-w-4xl mx-auto px-4 py-8;
}

.header {
  @apply mb-8;
}

.title {
  @apply text-3xl font-bold text-gray-800 mb-4;
}

.filters {
  @apply flex gap-4;
}

.search-input {
  @apply flex-1 px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500;
}

.tag-filter {
  @apply px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500;
}
</style>
