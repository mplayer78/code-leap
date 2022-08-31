<script lang="ts">
import { computed } from 'vue'
import challenges from '../challenges/challenges'

export default {
    name: 'Challenge',
    props: ['challengeId'],
    setup(props) {
        const currentChallenge = computed(() => {
            return challenges.find(val => val.id === props.challengeId)
        })
        return {
            currentChallenge
        }
    }
}
</script>

<template>
  <div>
    <p>{{ currentChallenge?.description }}</p>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>