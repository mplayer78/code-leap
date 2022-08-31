<script setup lang="ts">
import challenges from '../challenges/challenges'

const props = defineProps({
    challengeId: String
})

</script>

<script>
export default {
    name: 'Challenge',
    props: ['challengeId'],
    setup(props) {
        console.log(props)
    }
}
</script>

<template>
  <div>
    <p></p>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>