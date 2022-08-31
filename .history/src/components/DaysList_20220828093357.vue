<script setup lang="ts">
import challenges from '../challenges/challenges'

defineProps<{ msg: string }>()

const introObj = intro();

</script>

<template>
  <ul>
    <li v-for="challenge, index in challenges" :key="challenge.id">
      Week {{index + 1}}
    </li>
  </ul>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
