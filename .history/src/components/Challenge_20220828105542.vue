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
    console.log('currentChallenge :>> ', currentChallenge.value);
    return currentChallenge.value
})

</script>

<template>
  <div>
    <p>{{ currentChallenge?.date }}</p>
    <p>{{ currentChallenge?.description }}</p>
    <p>{{ inputList }}</p>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>