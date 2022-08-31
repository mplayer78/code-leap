<script setup lang="ts">
import intro from '../challenges/intro'

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
