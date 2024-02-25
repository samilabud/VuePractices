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
    <button
        class="inline-flex items-center justify-center whitespace-nowrap rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 bg-primary text-primary-foreground hover:bg-primary/90 h-10 px-4 py-2 ml-auto"
        @click="increase">Increase!</button>
    <button @click="decrease">Decrease!</button>
</template>