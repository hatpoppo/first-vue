<script setup>
import { ref } from "vue";
const text = ref("")
</script>
<template>
  <div class="alert-box">
    <h2>AlertBox</h2>
    <slot />
  </div>
</template>
<style scoped>
.alert-box {
  color: #666;
  border: 1px solid red;
  border-radius: 4px;
  padding: 20px;
  background-color: #f8f8f8;
}

strong {
  color: red;
}
</style>