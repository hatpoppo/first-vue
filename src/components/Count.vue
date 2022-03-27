<script setup>
import { reactive, ref } from 'vue';
const state = reactive({ count: 0 })
const count = ref(0)

function increment() {
  state.count++
}
function incrementRef() {
  count.value++
}
</script>
<template>
  <button @click="increment">reactive sample:{{ state.count }}</button>
  <button @click="incrementRef">ref sample:{{ count }}</button>
</template>