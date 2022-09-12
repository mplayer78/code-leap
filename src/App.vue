<script setup lang="ts">

import { ref } from 'vue'
import Intro from './components/Intro.vue'
import DaysList from './components/DaysList.vue'
import Challenge from './components/Challenge.vue'

const currentChallengeId = ref('');

function handleChallengeId(args: string) {
  currentChallengeId.value = args;
}

</script>

<script lang="ts">

export default {
  name: 'App',
  data() {
    return {
      player: null as null | HTMLAudioElement,
    }
  },
  methods: {
    handleChallengeId(args: string) {
      currentChallengeId.value = args;
    },
    handlePlay() {
      this.player?.play()
    }
  },
  mounted() {
    const p = this.$refs.audioplayer;

    if (p) {
      this.player = p as HTMLAudioElement
    }
  },
}
</script>

<template>
  <Intro/>
  <DaysList @challengeId="handleChallengeId"/>
  <Challenge :challengeId="currentChallengeId"/>
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
