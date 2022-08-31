<script lang="ts">
import { computed } from 'vue'
import challenges from '../challenges/challenges'

export default {
    name: 'Challenge',
    props: ['challengeId'],
    setup(props) {
        const currentChallenge = computed(() => {
            return challenges[props.challengeId]
        })
        console.log('currentChallenge :>> ', currentChallenge);
    }
}
</script>

<template>
  <div>
    <p></p>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>