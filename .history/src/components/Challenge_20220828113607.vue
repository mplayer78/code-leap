<script setup lang="ts">
import { computed, ref } from 'vue'
import challenges from '../challenges/challenges'

const props = defineProps({
    challengeId: String
})

const currentChallenge = computed(() => {
    return challenges.find(val => val.id === props.challengeId)
})

const inputList = computed(() => {
    return currentChallenge.value?.puzzleInput.join(', ')
})

const handleSubmit = (e) => {
    e.preventDefault();
    if (checkAnswer()) {
        message.value = currentChallenge.value.messages.success
    } else {
        message.value = currentChallenge.value.messages.failure
    };
}

const message = ref('');

const checkAnswer = () => {
    return [val1.value, val2.value].every(v => currentChallenge.value.puzzleInput.includes(v)) &&
    val1.value + val2.value === currentChallenge.value.target
}

const val1 = ref(0)
const val2 = ref(1)

</script>

<template>
  <div>
    <p>{{ currentChallenge?.date }}</p>
    <p>{{ currentChallenge?.description }}</p>
    <p>{{ inputList }}</p>
    <form action="POST" @submit="handleSubmit">
        <input type="number" v-model="val1">
        <input type="number" v-model="val2">
        <button type="submit">Go</button>
    </form>
    <p>{{ message }}</p>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>