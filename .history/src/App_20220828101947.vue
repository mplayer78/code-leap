<script setup lang="ts">

import { ref } from 'vue'
import Intro from './components/Intro.vue'
import DaysList from './components/DaysList.vue'
import Challenge from './components/Challenge.vue'

</script>

<script lang="ts">
export default {
  name: 'App',
  setup() {
    const currentChallengeId = ref('');

    return {
      currentChallengeId
    }
  },
  methods: {
    handleChallengeId(args: string) {
      this.currentChallengeId = args
      console.log('args :>> ', args);
      console.log('this.currentChallengeId :>> ', this.currentChallengeId);
    }
  }
}
</script>

<template>
  <Intro/>
  <DaysList @challengeId="handleChallengeId"/>
  <Challenge :challengeId="currentChallengeId"/>
  {{ currentChallengeId }}
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
