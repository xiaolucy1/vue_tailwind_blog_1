<template>
  <div class="tags-container">
    <div v-for="tag in tags" :key="tag" class="tag">
      {{ tag }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const tags = ref<string[]>(['Vue', 'TypeScript', 'Tailwind'])
</script>

<style scoped>
.tags-container {
  @apply flex flex-wrap gap-2;
}

.tag {
  @apply px-3 py-1 bg-gray-100 rounded-full text-sm text-gray-700;
}
</style>
