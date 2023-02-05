<template>
    <div class="login  w-screen h-screen bg-white dark:bg-gray-800">
        <div class="flex flex-col items-center gap-4">        
            <h1 class="text-4xl text-black text-center dark:text-white">
                Login Page
            </h1>
            <nuxt-img src="/login.png" loading="lazy" width="100"/>
        </div>
        <form class="flex flex-col items-center py-10 gap-1 text-black dark:text-white" @submit.prevent="login">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="email" placeholder="Enter email" required/>
            <label for="password">Password</label>
            <input type="password" id="password" v-model="password" placeholder="Enter password" required />
            <button type="submit" class="bg-orange-500 text-white border-black border-2 py-2 px-5">Login</button>
        </form>
        <div class="flex flex-row items-center justify-center gap-2 py-8">
            <button class="bg-orange-500 text-white border-black border-2 py-2 px-5" @click="setColorTheme($colorMode.preference == 'dark' ? 'light' : 'dark')">
                <Icon name="material-symbols:dark-mode" v-if="$colorMode.value == 'dark'" />
                <Icon name="material-symbols:light-mode" v-else />
            </button>
        </div>
    </div>
</template>

<script setup>

//let Theme = 'light' | 'dark';
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
