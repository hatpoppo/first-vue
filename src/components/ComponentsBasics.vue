<script setup>
import { ref } from "vue";
import BlogPost from './BlogPost.vue'

const posts = ref([
  { id: 1, title: 'My Page' },
  { id: 2, title: 'Your Page' },
  { id: 3, title: 'All Pages' }
])
</script>
<template>
  <div class="parts">
    <h2>ComponentsBasics</h2>
    <BlogPost v-for="post in posts" :key="post.id" :title="post.title" />
  </div>
</template>