<script setup>
import { isCoreComponent } from '@vue/compiler-core';
import { ref, reactive, computed } from 'vue';
const isActive = ref(true)
const hasError = ref(true)
const error = ref(null)
const classObject = reactive({
  active: true,
  'text-danger': true,
})
const computedClassObject = computed(() => ({
  active: isActive.value && !error.value,
  'text-danger': error.value && error.value.type === 'fatal'
}))
const activeClass = ref('active')
const errorClass = ref('text-danger')
const activeColor = ref('red')
const fontSize = ref(30)
</script>
<template>
  <div :class="{ active: isActive, 'text-danger': hasError }">ラーメン</div>
  <div :class="classObject">うどん</div>
  <div :class="computedClassObject">そば</div>
  <div :class="[activeClass, errorClass]">そうめん</div>
  <div :style="{ color: activeColor, 'font-size': fontSize + 'px' }">パスタ</div>
</template>
<style scoped>
.active {
  font-size: 1.2rem;
}
.text-danger {
  color: red;
}
</style>