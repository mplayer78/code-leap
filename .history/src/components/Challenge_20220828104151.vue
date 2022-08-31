<script lang="ts">
import { computed } from 'vue'
import challenges from '../challenges/challenges'

export default {
    name: 'Challenge',
    props: ['challengeId'],
    setup(props) {
        const currentChallenge = computed(() => {
            console.log('props :>> ', props.challengeId);
            return challenges[0]
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