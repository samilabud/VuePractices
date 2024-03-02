<template>
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" @submit.prevent="handleSubmit">
        <div class="rounded-lg border bg-gray-100 text-black shadow-sm w-full max-w-md mx-auto">
            <div class="flex flex-col space-y-1.5 p-6">
                <h3 class="text-2xl font-semibold whitespace-nowrap leading-none tracking-tight">Contact us</h3>
                <p class="text-sm text-gray-500">
                    Enter your information below and we'll get back to you as soon as we can.
                </p>
            </div>
            <div class="p-6">
                <div class="space-y-4">
                    <div class="grid grid-cols-2 gap-4">
                        <div class="space-y-2">
                            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 float-left"
                                for="first-name">
                                First name
                            </label>
                            <input ref="inputFirstName" :class="{ input_error: firstNameError }" class="input"
                                id="first-name" placeholder="Enter your first name" v-model.trim="firstName" />
                            <p v-if="firstNameError" class="text-red-500 text-xs italic">{{ firstNameError }}</p>
                        </div>
                        <div class="space-y-2">
                            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 float-left"
                                for="last-name">
                                Last name
                            </label>
                            <input class="input" id="last-name" placeholder="Enter your last name"
                                v-model.trim="lastName" />
                        </div>
                    </div>
                    <div class="space-y-2">
                        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 float-left"
                            for="email">
                            Email
                        </label>
                        <input class="fullinput" id="email" placeholder="Enter your email" type="email"
                            v-model.trim.lazy="email" />
                    </div>
                    <div class="space-y-2">
                        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 float-left"
                            for="message">
                            Message
                        </label>
                        <textarea class="fullinput min-h-[100px]" id="message" placeholder="Enter your message"
                            v-model="message"></textarea>
                    </div>
                    <div class="space-y-2">
                        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 float-left"
                            for="message">
                            Favorite Frontend Language
                        </label>
                        <div class="block justify-between w-28">
                            <input type="radio" name="language" value="Vue" id="vue" v-model="language" />
                            <label class="tracking-wide text-gray-700 text-xs font-bold" for="vue">
                                Vue
                            </label>
                            <div class="w-3 inline-block"></div>
                            <input type="radio" name="language" value="React" id="react" v-model="language" />
                            <label class="tracking-wide text-gray-700 text-xs font-bold" for="react">
                                React
                            </label>
                        </div>
                    </div>
                    <div class="space-y-2">
                        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 float-left"
                            for="places">
                            Favorite Place in DR
                        </label>
                        <div class="justify-between block">
                            <select name="places" class="selectinput" id="places" v-model="places">
                                <option value="" disabled selected>Select a place</option>
                                <option>Constanza</option>
                                <option>Samaná</option>
                                <option>Punta Cana</option>
                                <option>Otro</option>
                            </select>
                        </div>
                    </div>
                    <div class="space-y-2">
                        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 float-left"
                            for="message">
                            Favorite Fruits
                        </label>
                        <div class="flex justify-between px-3 clear-start">
                            <input type="checkbox" id="strawberry" value="Strawberry" v-model="fruits" />
                            <label for="strawberry">Strawberry</label>

                            <input type="checkbox" id="apple" value="Apple" v-model="fruits" />
                            <label for="apple">Apple</label>

                            <input type="checkbox" id="grape" value="Grape" v-model="fruits" />
                            <label for="grape">Grape</label>

                            <input type="checkbox" id="blueberry" value="Blueberry" v-model="fruits" />
                            <label for="blueberry">Blueberry</label>
                        </div>
                    </div>
                </div>
            </div>
            <div class="flex items-center p-6 justify-end">
                <button class="button">
                    Send message
                </button>
            </div>
            <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert"
                v-if="hasError && formStatusMessage">
                <strong class="font-bold">Holy smokes! </strong>
                <span class="block sm:inline">{{ formStatusMessage }}</span>
                <span class="absolute top-0 bottom-0 right-0 px-4 py-3">
                    <svg class="fill-current h-6 w-6 text-red-500" role="button" xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 20 20" @click="cleanErrorMessages">
                        <title>Close</title>
                        <path
                            d="M14.348 14.849a1.2 1.2 0 0 1-1.697 0L10 11.819l-2.651 3.029a1.2 1.2 0 1 1-1.697-1.697l2.758-3.15-2.759-3.152a1.2 1.2 0 1 1 1.697-1.697L10 8.183l2.651-3.031a1.2 1.2 0 1 1 1.697 1.697l-2.758 3.152 2.758 3.15a1.2 1.2 0 0 1 0 1.698z" />
                    </svg>
                </span>
            </div>
            <div class="flex items-center bg-blue-500 text-white text-sm font-bold px-4 py-3" role="alert"
                v-if="!hasError && formStatusMessage">
                <svg class="fill-current w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                    <path
                        d="M12.432 0c1.34 0 2.01.912 2.01 1.957 0 1.305-1.164 2.512-2.679 2.512-1.269 0-2.009-.75-1.974-1.99C9.789 1.436 10.67 0 12.432 0zM8.309 20c-1.058 0-1.833-.652-1.093-3.524l1.214-5.092c.211-.814.246-1.141 0-1.141-.317 0-1.689.562-2.502 1.117l-.528-.88c2.572-2.186 5.531-3.467 6.801-3.467 1.057 0 1.233 1.273.705 3.23l-1.391 5.352c-.246.945-.141 1.271.106 1.271.317 0 1.357-.392 2.379-1.207l.6.814C12.098 19.02 9.365 20 8.309 20z" />
                </svg>
                <p>{{ formStatusMessage }}</p>
            </div>
        </div>
    </form>
    <p class="text-center text-gray-500 text-xs">
        &copy;2024 Samil Abud. All rights reserved.
    </p>
    <div class="rounded-lg border bg-gray-100 text-black shadow-sm w-full max-w-md mx-auto pb-5">
        <h3 class="text-lg font-semibold">Live answers</h3>
        <div v-if="firstName || lastName">
            <strong>Name:</strong> <span>{{ firstName }} {{ lastName }}</span>
        </div>
        <div v-if="email">
            <strong>Email:</strong><span>{{ email }}</span>
        </div>
        <div v-if="message">
            <strong>Message:</strong>
            <p style="white-space: pre-line;">{{ message }}</p>
        </div>
        <div v-if="language">
            <strong>Favorite language:</strong><span>{{ language }}</span>
        </div>
        <div v-if="places">
            <strong>Favorite place:</strong><span>{{ places }}</span>
        </div>
        <div v-if="fruits.length > 0">
            <strong>Favorite fruits: </strong><span>{{ fruits.join(',') }}</span>
        </div>
    </div>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue'

const inputFirstName = ref(null);
const firstName = ref('');
const lastName = ref('')
const email = ref('')
const message = ref('');
const language = ref('')
const places = ref('')
const fruits = ref([])

const firstNameError = ref('')

const hasError = ref(false);
const formStatusMessage = ref("");

const runValidations = () => {
    firstNameError.value = firstName.value === "" ? "Should has a first name!" : "";
}
watch(firstName, () => {
    runValidations()
})

const handleSubmit = () => {
    hasError.value = false
    runValidations();
    if (!firstNameError.value) {
        formStatusMessage.value = "Form submited!";
    } else {
        hasError.value = true;
        formStatusMessage.value = "Should fix errors!";
    }
}

const cleanErrorMessages = () => {
    formStatusMessage.value = "";
    hasError.value = false;
}

onMounted(() => {
    inputFirstName.value.focus();
})
</script>