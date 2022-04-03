<script setup>
import { ref, onMounted } from "vue";
const input = ref(null)
onMounted(() => {
  input.value.focus()
  // console.log({ 'itemRefs': itemRefs.value.map(i => i.textContent) })
  console.log({ 'itemRefs': itemRefs.value })
})
const lists = ref([1, 2, 3, 4])
const itemRefs = ref([])
</script>
<template>
  <div class="parts">
    <h2>TemplateRefs</h2>
    <input ref="input" />
    <ul>
      <li v-for="list in lists" ref="itemRef">{{ list }}</li>
    </ul>
  </div>
</template>