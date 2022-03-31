<script setup>
import { ref } from "vue"
const count = ref(0)
const name = ref("Vue.js")
function greeting(event) {
  alert(`Hello ${name.value}`)
  if (event) {
    alert(event.target.tagName)
  }
}
</script>
<template>
  <button @click="count++">Add 1</button>
  <p>Count is :{{ count }}</p>
  <button @click="greeting">Greet</button>
</template>