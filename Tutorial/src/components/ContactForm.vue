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
                        <input class="input" id="first-name" placeholder="Enter your first name" />
                    </div>
                    <div class="space-y-2">
                        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="last-name">
                            Last name
                        </label>
                        <input class="input" id="last-name" placeholder="Enter your last name" />
                    </div>
                </div>
                <div class="space-y-2">
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="email">
                        Email
                    </label>
                    <input class="fullinput" id="email" placeholder="Enter your email" type="email" />
                </div>
                <div class="space-y-2">
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="message">
                        Message
                    </label>
                    <textarea class="fullinput min-h-[100px]" id="message" placeholder="Enter your message"></textarea>
                </div>
                <div class="space-y-2">
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="message">
                        Favorite Frontend Language
                    </label>
                    <div class="flex justify-between w-28">
                        <input type="radio" name="language" value="Vue" id="vue" />
                        <label class="block tracking-wide text-gray-700 text-xs font-bold" for="vue">
                            Vue
                        </label>
                        <input type="radio" name="language" value="React" id="react" />
                        <label class="block tracking-wide text-gray-700 text-xs font-bold" for="react">
                            React
                        </label>
                    </div>
                </div>
                <div class="space-y-2">
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="message">
                        Favorite Place in DR
                    </label>
                    <div class="flex justify-between">
                        <select name="places" class="selectinput">
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
                        Favorites Fruits
                    </label>
                    <div class="flex justify-between px-3">
                        <input type="checkbox" id="strawberry" value="Strawberry" />
                        <label for="strawberry">Strawberry</label>

                        <input type="checkbox" id="apple" value="Apple" />
                        <label for="apple">Apple</label>

                        <input type="checkbox" id="grape" value="Grape" />
                        <label for="grape">Grape</label>

                        <input type="checkbox" id="blueberry" value="Blueberry" />
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
</template>

<script setup>

</script>