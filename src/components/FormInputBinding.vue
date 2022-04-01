<script setup>
import { ref } from "vue";
const text = ref("")
const text_model = ref("")
const textarea_model = ref("")
const checked = ref(false)
</script>
<template>
  <input :value="text" @input="event => text = event.target.value" />
  <p>入力データは {{ text }} です。</p>
  <input v-model="text_model" />
  <p>入力データは {{ text_model }} です。</p>

  <textarea v-model="textarea_model"></textarea>
  <textarea>入力データは {{ textarea_model }} です。</textarea>
  <input type="checkbox" id="checkbox" v-model="checked" />
  <label for="checked">{{ checked }}</label>
</template>