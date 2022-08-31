<script setup lang="ts">
import challenges from '../challenges/challenges.json'

const getIsCompleted = (id: string): boolean => {
  return !!window.localStorage.getItem(id);
}

</script>

<template>
  <ul>
    <li v-for="challenge, index in challenges" :key="challenge.id" class="challengeList">
      <button @click="$emit('challengeId', challenge.id)">
        Week {{index + 1}}
        {{challenge.id}}
        <span v-if="getIsCompleted(challenge.id)">👌</span>
      </button>
    </li>
  </ul>
</template>

<style scoped>
.challengeList {
  list-style: none;
}
</style>
