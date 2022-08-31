<script setup lang="ts">
import { computed } from 'vue'
import challenges from '../challenges/challenges'

const props = defineProps({
    challengeId: String
})

const currentChallenge = computed(() => {
    return challenges.find(val => val.id === props.challengeId)
})

const inputList = computed(() => {
    return currentChallenge.value.puzzleInput.join(', ')
})

const handleSubmit = (e) => {
    e.preventDefault();
    console.log('val :>> ', e);
}

</script>

<template>
  <div>
    <p>{{ currentChallenge?.date }}</p>
    <p>{{ currentChallenge?.description }}</p>
    <p>{{ inputList }}</p>
    <form action="POST" @submit="handleSubmit">
        <input type="text">
        <input type="text">
        <button type="submit">Go</button>
    </form>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>