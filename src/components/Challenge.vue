<script setup lang="ts">
import { computed, ref } from 'vue'
import challenges from '../challenges/challenges.json'
import { marked } from 'marked';

const props = defineProps({
    challengeId: String
})

const currentChallenge = computed(() => {
    return challenges.find(val => val.id === props.challengeId)
})

const inputList = computed(() => {
    if (Array.isArray(currentChallenge.value?.puzzleInput)) {
        return currentChallenge.value?.puzzleInput.join(', ')        
    } else {
        return currentChallenge.value?.puzzleInput
    }
})

const handleSubmit = (e: Event) => {
    e.preventDefault();
    if (checkAnswer()) {
        handleCorrect(props.challengeId ?? "", val1.value, val2.value);
        message.value = currentChallenge.value?.messages.success ?? ""
    } else {
        message.value = currentChallenge.value?.messages.failure ?? ""
    };
}

const handleCorrect = (id: string, ...args: any[]) => {
    showSubmit.value = true;
    window.localStorage.setItem(id, JSON.stringify(args))
    fetch("/", {
        method: "POST",
        headers: { "Content-Type": "application/x-www-form-urlencoded" },
    })
    .catch((error) => alert(error));
}

const displayDescription = computed(() => {
    return marked(currentChallenge.value?.description.replace("%target%", String(currentChallenge.value?.target) ?? "") || "");
})

const message = ref('');

const val1 = ref(0)
const val2 = ref(0)

const checkAnswer = () => {
    switch (currentChallenge.value?.check) {
        case "eq_sum_of_given":
            const vals = [val1.value, val2.value];
            // @ts-ignore
            return vals.every(v => currentChallenge.value?.puzzleInput?.find(pi => v === pi)) &&
            val1.value + val2.value === currentChallenge.value?.target
        case "eq_sum":
        default:
            return val1.value + val2.value === currentChallenge.value?.target
    }
}

const showSubmit = ref(false)

</script>

<template>
  <div>
    <p>{{ currentChallenge?.date }}</p>
    <p v-html="displayDescription"></p>
    <p class="input">{{ inputList }}</p>
    <form action="POST" @submit="handleSubmit" v-if="currentChallenge?.id">
        <input type="number" v-model="val1">
        <input type="number" v-model="val2">
        <button type="submit">Go</button>
    </form>
    <p>{{ message }}</p>
    <form
    name="ask-question"
    method="post"
    data-netlify="true"
    data-netlify-honeypot="bot-field"
    v-if="showSubmit"
    >
    <input type="hidden" name="form-name" value="ask-question" />
    <button>Submit</button>
  </form>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}

.input {
    line-break: anywhere;
}
</style>