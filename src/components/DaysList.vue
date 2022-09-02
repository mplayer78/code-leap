<script setup lang="ts">
import challenges from '../challenges/challenges.json'

const getIsCompleted = (id: string): boolean => {
  return !!window.localStorage.getItem(id);
}

</script>

<template>
  <ul class="challenge__list">
    <li v-for="challenge, index in challenges" :key="challenge.id" class="challenge__item">
      <button @click="$emit('challengeId', challenge.id)" :class="getIsCompleted(challenge.id) ? 'week-button__done' : ''">
        Week {{index + 1}}
        <span v-if="getIsCompleted(challenge.id)">👌</span>
      </button>
    </li>
  </ul>
</template>

<style scoped>
.challenge__list {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  padding: 0;
  justify-content: center;
}
.challenge__item {
  list-style: none;
}

.week-button__done {
  background: #A3DA9A;
}
</style>
