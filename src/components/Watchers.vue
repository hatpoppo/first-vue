<script setup>
import { ref, watch, watchEffect } from "vue";
const question = ref("")
const answer = ref('Questions usually contain a question mark. ')
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.indexOf('?') > -1) {
    answer.value = 'Thinking ...'
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    } catch (error) {
      answer.value = 'Error! Could not reach the API. ' + error
    }
  }
})
const x = ref(0)
const y = ref(0)
//single ref
watch(x, (newX) => {
  console.log(`x is ${newX}.`)
})
//getter
watch(() => x.value + y.value, (sum) => {
  console.log(`sum of x + y is:${sum}`)
})
//array ob multiple sources
watch([x, () => y.value], ([newX, newY]) => {
  console.log(`x is ${newX} and y is ${newY}.`)
})

const API_URL = `https://api.github.com/repos/vuejs/core/commits?per_page=3&sha=`
const branches = ['main', 'v2-compat']

const currentBranch = ref(branches[0])
const commits = ref(null)

watchEffect(async () => {
  // this effect will run immediately and then
  // re-run whenever currentBranch.value changes
  const url = `${API_URL}${currentBranch.value}`
  commits.value = await (await fetch(url)).json()
})

function truncate(v) {
  const newline = v.indexOf('\n')
  return newline > 0 ? v.slice(0, newline) : v
}

function formatDate(v) {
  return v.replace(/T|Z/g, ' ')
}
</script>
<template>
  <div class="parts">
    <h2>Watchers</h2>
    <p>
      Ask a yes/no question:
      <input v-model="question" />
    </p>
    <p>{{ answer }}</p>
    <p>
      x:
      <input v-model="x" />
      y:
      <input v-model="y" />
    </p>

    <template v-for="branch in branches">
      <input type="radio" :id="branch" :value="branch" name="branch" v-model="currentBranch" />
      <label :for="branch">{{ branch }}</label>
    </template>
    <p>vuejs/vue@{{ currentBranch }}</p>
    <ul>
      <li v-for="{ html_url, sha, author, commit } in commits">
        <a :href="html_url" target="_blank" class="commit">{{ sha.slice(0, 7) }}</a>
        -
        <span class="message">{{ truncate(commit.message) }}</span>
        <br />by
        <span class="author">
          <a :href="author.html_url" target="_blank">{{ commit.author.name }}</a>
        </span>
        at
        <span class="date">{{ formatDate(commit.author.date) }}</span>
      </li>
    </ul>
  </div>
</template>