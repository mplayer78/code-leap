<script setup lang="ts">
import challenges from '../challenges/challenges'

defineProps<{ msg: string }>()

const introObj = intro();

</script>

<template>
  <ul>
    <li v-for="(index, challenge) in challenges" :key="challenge.id">
      Hello World
    </li>
  </ul>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
