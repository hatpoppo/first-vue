<script setup>
import { ref } from "vue";
defineProps(['title'])
</script>
<template>
  <div class="parts">
    <h2>BlogPost</h2>
    <p>{{ title }}</p>
  </div>
</template>