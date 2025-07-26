<script setup lang="ts">
import { reactive, ref } from 'vue'

defineProps<{
  msg: string
}>()

const testR = ref(0)
const check = ref(true)
const userInput = ref('')
const myObject = reactive({
  title: 'Vue에서 목록을 작성하는 방법',
  author: '홍길동',
  publishedAt: '2016-04-10',
})

const selected = ref('1')

const options = ref([
  { text: '하나', value: '1' },
  { text: '둘', value: '2' },
  { text: '셋', value: '3' },
])

const chnageCheck = () => {
  check.value = !check.value
}

function hiAlert(event: MouseEvent) {
  console.log(event)
  alert(`Hello, ${'YOU'}!`)
}

function inputEnter() {
  console.log(userInput.value)
}
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vite.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <button @click.stop.prevent="hiAlert">HIHI</button>
    <button @click="chnageCheck">Click!</button>
    <p v-if="check">{{ testR }}</p>
    <p v-else>{{ testR + 1 }}</p>
    <ul>
      <li v-for="(value, key) in myObject">{{ key }} : {{ value }}</li>
    </ul>
    <input @keyup.enter="inputEnter" v-model="userInput" />
    <select v-model="selected">
      <option v-for="option in options" :value="option.value">
        {{ option.text }}
      </option>
    </select>

    <div>선택됨: {{ selected }}</div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
