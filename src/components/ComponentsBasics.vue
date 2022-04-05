<script setup>
import { ref } from "vue";
import BlogPost from './BlogPost.vue'
import AlertBox from './AlertBox.vue'
import Home from './tab/Home.vue'
import Posts from './tab/Posts.vue'

const posts = ref([
  { id: 1, title: 'My Page' },
  { id: 2, title: 'Your Page' },
  { id: 3, title: 'All Pages' }
])
const postFontSize = ref(1)
const currentTab = ref('Home')
const tabs = {
  Home,
  Posts
}
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
    <AlertBox>Something bad happened.</AlertBox>
    <div class="demo">
      <button
        v-for="(_, tab) in tabs"
        :key="tab"
        :class="['tab-button', { active: currentTab === tab }]"
        @click="currentTab = tab"
      >{{ tab }}</button>
      <component :is="tabs[currentTab]" class="tab"></component>
    </div>
  </div>
</template>
<style>
.demo {
  font-family: sans-serif;
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 40px;
  user-select: none;
  overflow-x: auto;
}

.tab-button {
  padding: 6px 10px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border: 1px solid #ccc;
  cursor: pointer;
  background: #f0f0f0;
  margin-bottom: -1px;
  margin-right: -1px;
}
.tab-button:hover {
  background: #e0e0e0;
}
.tab-button.active {
  background: #e0e0e0;
}
.tab {
  border: 1px solid #ccc;
  padding: 10px;
}
</style>