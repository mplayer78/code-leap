<script setup lang="ts">
import challenges from '../challenges/challenges'

</script>

<template>
  <ul>
    <li v-for="challenge, index in challenges" :key="challenge.id">
      <button @click="$emit('challengeId', challenge.id)">Week {{index + 1}}</button>
    </li>
  </ul>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
