<script setup>
import { ref, reactive } from "vue";
const parentMessage = ref("Parent")
const items = ref([{ message: "foo" }, { message: "bar" }])
const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})
</script>
<template>
  <ul>
    <li v-for="(item, index) in items">{{ parentMessage }} - {{ index }} - {{ item.message }}</li>
  </ul>
  <ul>
    <li v-for="(value, key) in myObject">{{ key }} : {{ value }}</li>
  </ul>
</template>