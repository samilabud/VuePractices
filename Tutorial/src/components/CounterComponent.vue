<script setup>
import { ref, watch } from 'vue'

const counter = ref(0);

watch(counter, () => {
    if (counter.value < 0) {
        counter.value = 0
    }
})

const increase = () => {
    counter.value++
}

const decrease = () => {
    counter.value--
}

</script>

<template>
    <p><span>{{ counter }}</span></p>
    <button @click="increase">Increase!</button>
    <button @click="decrease">Decrease!</button>
</template>