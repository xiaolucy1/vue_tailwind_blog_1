<template>
  <div class="flex flex-col items-center w-[70%] mx-auto">
    <BlogTitle />
    <BlogImage />
    <BlogPosts />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BlogTitle from './components/BlogTitle.vue';
import BlogImage from './components/BlogImage.vue';
import BlogPosts from './components/BlogPosts.vue'

export default defineComponent({
  name: "App",
  components: {
    BlogTitle,
    BlogImage,
    BlogPosts,
  },
});
</script>
