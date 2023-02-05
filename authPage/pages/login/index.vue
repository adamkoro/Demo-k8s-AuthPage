<template>
    <div class="login">
        <div class="flex flex-col items-center gap-4">        
            <h1 class="text-4xl text-black text-center">
                Login Page
            </h1>
            <img src="~/assets/login.png" width="90"/>
        </div>
        <!-- Create a login form-->
        <form class="flex flex-col items-center py-10 gap-1" @submit.prevent="login">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="email" placeholder="Enter email" required/>
            <label for="password">Password</label>
            <input type="password" id="password" v-model="password" placeholder="Enter password" required />
            <button type="submit" class="bg-orange-500 text-white border-black border-2 py-2 px-5">Login</button>
        </form>
    </div>
</template>

<script setup>

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
