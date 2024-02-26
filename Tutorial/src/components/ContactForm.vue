<template>
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
                        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="first-name">
                            First name
                        </label>
                        <input class="input" id="first-name" placeholder="Enter your first name" v-model="firstName" />
                    </div>
                    <div class="space-y-2">
                        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="last-name">
                            Last name
                        </label>
                        <input class="input" id="last-name" placeholder="Enter your last name" v-model="lastName" />
                    </div>
                </div>
                <div class="space-y-2">
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="email">
                        Email
                    </label>
                    <input class="fullinput" id="email" placeholder="Enter your email" type="email" v-model="email" />
                </div>
                <div class="space-y-2">
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="message">
                        Message
                    </label>
                    <textarea class="fullinput min-h-[100px]" id="message" placeholder="Enter your message"
                        v-model="message"></textarea>
                </div>
                <div class="space-y-2">
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="message">
                        Favorite Frontend Language
                    </label>
                    <div class="flex justify-between w-28">
                        <input type="radio" name="language" value="Vue" id="vue" v-model="language" />
                        <label class="block tracking-wide text-gray-700 text-xs font-bold" for="vue">
                            Vue
                        </label>
                        <input type="radio" name="language" value="React" id="react" v-model="language" />
                        <label class="block tracking-wide text-gray-700 text-xs font-bold" for="react">
                            React
                        </label>
                    </div>
                </div>
                <div class="space-y-2">
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="places">
                        Favorite Place in DR
                    </label>
                    <div class="flex justify-between">
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
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="message">
                        Favorite Fruits
                    </label>
                    <div class="flex justify-between px-3">
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
    </div>
    <div class="rounded-lg border bg-gray-100 text-black shadow-sm w-full max-w-md mx-auto">
        <div v-if="firstName || lastName">
            <stong>Name:</stong> <span>{{ firstName }} {{ lastName }}</span>
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
import { ref } from 'vue'

const firstName = ref('');
const lastName = ref('')
const email = ref('')
const message = ref('');
const language = ref('')
const places = ref('')
const fruits = ref([])
</script>