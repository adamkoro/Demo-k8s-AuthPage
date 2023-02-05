<template>
    <div class="login  w-screen h-screen bg-white dark:bg-gray-800">
        <div class="flex flex-col items-center gap-4">        
            <h1 class="text-4xl text-black text-center dark:text-white">
                Login Page
            </h1>
            <img src="~/assets/login.png" width="90"/>
        </div>
        <!-- Create a login form-->
        <form class="flex flex-col items-center py-10 gap-1 text-black dark:text-white" @submit.prevent="login">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="email" placeholder="Enter email" required/>
            <label for="password">Password</label>
            <input type="password" id="password" v-model="password" placeholder="Enter password" required />
            <button type="submit" class="bg-orange-500 text-white border-black border-2 py-2 px-5">Login</button>
        </form>
        <!-- Create theme switcher button -->
        <div class="flex flex-row items-center justify-center gap-2 py-8">
            <button class="bg-orange-500 text-white border-black border-2 py-2 px-5" @click="setColorTheme('light')">Light</button>
            <button class="bg-orange-500 text-white border-black border-2 py-2 px-5" @click="setColorTheme('dark')">Dark</button>
        </div>
    </div>
</template>

<script setup>

let Theme = 'light' | 'dark';
const setColorTheme = (Theme) => {
    useColorMode().preference = Theme;
}

useHead({
    title: `Login Page`,
    link: [{ hid: 'icon', rel: 'icon', type: 'image/svg', href: '/favicon.svg' }]
})

// Define variables
let email = "";
let password = "";

// Define functions
async function login() {
    try {
        const response = await this.$auth.loginWith("local", {
            data: {
                email,
                password,
            },
        });
        console.log(response);
    } catch (error) {
        console.log(error);
    }
}
</script>
