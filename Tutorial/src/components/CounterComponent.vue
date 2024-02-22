<script setup>
import { ref } from 'vue'

const counter = ref(0);

const increase = () => {
    counter.value++
}

</script>

<template>
    <p><span>{{ counter }}</span></p>
    <button @click="increase">Increase!</button>
</template>