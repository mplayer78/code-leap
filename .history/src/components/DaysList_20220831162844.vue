<script setup lang="ts">
import challenges from '../challenges/challenges.json'

</script>

<template>
  <ul>
    <li v-for="challenge, index in challenges" :key="challenge.id" class="challengeList">
      <button @click="$emit('challengeId', challenge.id)">Week {{index + 1}}</button>
    </li>
  </ul>
</template>

<style scoped>
.challengeList {
  list-style: none;
}
</style>
