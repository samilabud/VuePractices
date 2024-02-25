<script setup>
import { ref } from 'vue'

const lastId = ref(2);
const inputTask = ref("");
const todos = ref([{ id: 1, name: "Go to the supermarket", done: false }, { id: 2, name: "Fix frontend bug", done: true }])

const addTask = () => {
    if (inputTask.value !== "") {
        lastId.value++;
        todos.value.push({ id: lastId.value, name: inputTask.value, done: false })
        inputTask.value = ""
    } else {
        alert("Please type a task!")
    }
}

const removeTask = (id) => {
    todos.value = todos.value.filter(todo => todo.id !== id)
}

const markAsDone = (id) => {
    todos.value = todos.value.map(todo => {
        if (todo.id === id) {
            todo.done = true
        }
        return todo
    })
}
</script>

<template>
    <form @submit.prevent="addTask">
        <label for="task">Task:</label><input class="input" v-model="inputTask" id="task" />
        <button class="button">Add task</button>
    </form>
    <ul class="todolist">
        <li v-for="todo in todos" :key="todo.id">
            <span :class="{ taskDone: todo.done }">{{ todo.name }} </span>
            <button class="button" v-if="!todo.done" @click="markAsDone(todo.id)">Done!</button>
            <button class="button" @click="removeTask(todo.id)">X</button>
        </li>
    </ul>
</template>

<style>
.todolist {
    list-style: none;
}

.taskDone {
    text-decoration: line-through;
}
</style>