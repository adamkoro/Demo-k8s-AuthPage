<template>
    <div class="">
        <h1 class="text-4xl text-black">Auth Page</h1>
        <!-- Create a login form-->
        <form class="flex flex-col" @submit.prevent="login">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="email" />
            <label for="password">Password</label>
            <input type="password" id="password" v-model="password" />
            <button type="submit" class="bg-blue-500 text-white">Login</button>
        </form>

        <!-- Create a register form-->
        <form class="flex flex-col" @submit.prevent="register">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="email" />
            <label for="password">Password</label>
            <input type="password" id="password" v-model="password" />
            <button type="submit" class="bg-blue-500 text-white">Register</button>
        </form>

        <!-- Create a logout button-->
        <button @click="logout" class="bg-blue-500 text-white">Logout</button>

        <!-- Create a reset password form-->
        <form class="flex flex-col" @submit.prevent="resetPassword">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="email" />
            <button type="submit" class="bg-blue-500 text-white">Reset Password</button>
        </form>

        <!-- Create a change password form-->
        <form class="flex flex-col" @submit.prevent="changePassword">
            <label for="oldPassword">Old Password</label>
            <input type="password" id="oldPassword" v-model="oldPassword" />
            <label for="newPassword">New Password</label>
            <input type="password" id="newPassword" v-model="newPassword" />
            <button type="submit" class="bg-blue-500 text-white">Change Password</button>
        </form>
    </div>
</template>

<script>
// Define variables
let email = "";
let password = "";
let oldPassword = "";
let newPassword = "";

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

async function register() {
    try {
        const response = await this.$auth.registerWith("local", {
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

async function logout() {
    try {
        const response = await this.$auth.logout();
        console.log(response);
    } catch (error) {
        console.log(error);
    }
}

async function resetPassword() {
    try {
        const response = await this.$auth.requestPasswordRecovery(email);
        console.log(response);
    } catch (error) {
        console.log(error);
    }
}

</script>
