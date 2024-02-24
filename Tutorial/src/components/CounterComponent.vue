<script setup>
import { reactive, watch } from 'vue'

const counter = reactive({ number: 0 });

watch(counter, () => {
    if (counter.number < 0) {
        counter.number = 0
    }
})

const increase = () => {
    counter.number++
}

const decrease = () => {
    counter.number--
}

</script>

<template>
    <p><span>{{ counter.number }}</span></p>
    <button @click="increase">Increase!</button>
    <button @click="decrease">Decrease!</button>
</template>