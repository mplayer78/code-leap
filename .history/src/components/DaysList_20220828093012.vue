<script setup lang="ts">
import { ref } from 'vue'
import intro from '../challenges/intro'

defineProps<{ msg: string }>()

const introObj = intro();

</script>

<template>
  <h1>{{introObj.heading}}</h1>
  <h3>{{introObj.description}}</h3>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
