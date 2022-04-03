<script setup>
import { ref } from "vue";
import BlogPost from './BlogPost.vue'

const posts = ref([
  { id: 1, title: 'My Page' },
  { id: 2, title: 'Your Page' },
  { id: 3, title: 'All Pages' }
])
const postFontSize = ref(1)
</script>
<template>
  <div class="parts">
    <h2>ComponentsBasics</h2>
    <div :style="{ fontSize: postFontSize + 'em' }">
      <BlogPost
        v-for="post in posts"
        :key="post.id"
        :title="post.title"
        @enlarge-text="postFontSize += 0.1"
      />
    </div>
  </div>
</template>