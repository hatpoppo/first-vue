<script setup>
import { ref } from "vue";
defineProps(['title'])
defineEmits(['enlarge-text'])
</script>
<template>
  <div class="parts">
    <h2>BlogPost</h2>
    <p>{{ title }}</p>
    <button @click="$emit('enlarge-text')">Enlarge text</button>
  </div>
</template>