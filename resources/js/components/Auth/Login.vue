<template>
    <form @submit.prevent="submitLogin">
        <head>
  <style>
    form {
      background-color: lightblue;
    }
    .container {
      background-color: #f4a261; /* Hex code for color */
      padding: 20px;
      border-radius: 10px;
    }
  </style>
</head>
        <!-- Email -->
        <div>
            <label for="email" class="block text-sm font-medium text-gray-700">
                Email
            </label>
            <input
                v-model="loginForm.email"
                id="email"
                type="email"
                class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
                required
                autofocus
                autocomplete="username"
            />
            <!-- Validation Errors -->
            <div class="mt-1 text-red-600">
                <div v-for="message in validationErrors?.email">
                    {{ message }}
                </div>
            </div>
        </div>

        <!-- Password -->
        <div class="mt-4">
            <label
                for="password"
                class="block text-sm font-medium text-gray-700"
            >
                Password
            </label>
            <input
                v-model="loginForm.password"
                id="password"
                type="password"
                class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
                required
                autocomplete="current-password"
            />
            <!-- Validation Errors -->
            <div class="mt-1 text-red-600">
                <div v-for="message in validationErrors?.password">
                    {{ message }}
                </div>
            </div>
        </div>

        <!-- Remember me -->
        <div class="block mt-4">
            <label class="flex items-center">
                <input
                    type="checkbox"
                    name="remember"
                    v-model="loginForm.remember"
                    class="text-indigo-600 border-gray-300 rounded shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
                />
                <span class="ml-2 text-sm text-gray-600">Remember me</span>
            </label>
        </div>
        <!-- Buttons -->
        <div class="flex items-center justify-start mt-4">
            <button
                class="inline-flex items-center px-4 py-2 ml-4 text-xs font-semibold tracking-widest text-white uppercase transition duration-150 ease-in-out bg-gray-800 border border-transparent rounded-md hover:bg-gray-700 active:bg-gray-900 focus:outline-none focus:border-gray-900 focus:shadow-outline-gray"
                :class="{ 'opacity-25': processing }"
                :disabled="processing"
            >
                Login
            </button>
        </div>
        <div class="flex justify-end">
            <p class="p-1">Don't have account?</p>
            <router-link
                class="p-1 text-white bg-red-500 rounded-lg"
                :to="{ name: 'register' }"
                >Register</router-link
            >
        </div>
    </form>
</template>

<script setup>
import useAuth from "@/composables/auth";

const { loginForm, validationErrors, processing, submitLogin } = useAuth();
</script>
