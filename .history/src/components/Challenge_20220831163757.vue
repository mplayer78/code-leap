<script setup lang="ts">
import { computed, ref } from 'vue'
import challenges from '../challenges/challenges.json'

const props = defineProps({
    challengeId: String
})

const currentChallenge = computed(() => {
    return challenges.find(val => val.id === props.challengeId)
})

const inputList = computed(() => {
    return currentChallenge.value?.puzzleInput.join(', ')
})

const handleSubmit = (e: Event) => {
    e.preventDefault();
    if (checkAnswer()) {
        message.value = currentChallenge.value?.messages.success ?? ""
    } else {
        message.value = currentChallenge.value?.messages.failure ?? ""
    };
}

const displayDescription = computed(() => {
    return currentChallenge.value?.description.replace("%target%", String(currentChallenge.value?.target) ?? "")
})

const message = ref('');

const checkAnswer = () => {
    return [val1.value, val2.value].every(v => currentChallenge.value?.puzzleInput.includes(v)) &&
    val1.value + val2.value === currentChallenge.value?.target
}

const val1 = ref(0)
const val2 = ref(1)

</script>

<template>
  <div>
    <p>{{ currentChallenge?.date }}</p>
    <p>{{ displayDescription }}</p>
    <p>{{ inputList }}</p>
    <form action="POST" @submit="handleSubmit" v-if="currentChallenge?.id">
        <input type="number" v-model="val1">
        <input type="number" v-model="val2">
        <button type="submit">Go</button>
    </form>
    <p>{{ message }}</p>
    <form name="contact" netlify>
  <p>
    <label>Name <input type="text" name="name" /></label>
  </p>
  <p>
    <label>Email <input type="email" name="email" /></label>
  </p>
  <p>
    <button type="submit">Send</button>
  </p>
</form>

  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>