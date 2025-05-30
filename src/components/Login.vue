<template>
  <div class="flex items-center justify-center">
    <div
      class="w-[400px] h-[290px] bg-white/80 backdrop-blur-md rounded-2xl shadow-2xl p-10 border border-purple-200 flex flex-col justify-center"
    >
      <h2
        class="text-3xl font-extrabold mb-6 text-center text-purple-700 tracking-tight"
      >
        Sign In
      </h2>
      <form @submit.prevent="login" class="flex flex-col gap-4">
        <div>
          <label class="block text-purple-700 font-medium mb-1" for="email"
            >Email</label
          >
          <input
            v-model="email"
            type="email"
            id="email"
            class="w-full px-3 py-1.5 border border-purple-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-400 bg-purple-50 placeholder-purple-300 transition"
            placeholder="you@example.com"
            required
          />
        </div>
        <div>
          <label class="block text-purple-700 font-medium mb-1" for="password"
            >Password</label
          >
          <input
            v-model="password"
            type="password"
            id="password"
            class="w-full px-3 py-1.5 border border-purple-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-400 bg-purple-50 placeholder-purple-300 transition"
            placeholder="••••••••"
            required
          />
        </div>
        <button
          type="submit"
          class="w-full bg-gradient-to-r from-purple-500 to-fuchsia-500 text-white py-2 rounded-lg font-semibold shadow-md hover:from-purple-600 hover:to-fuchsia-600 transition"
        >
          Login
        </button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
localStorage.removeItem("loginStatus");
const router = useRouter();

const email = ref("");
const password = ref("");

function login() {
  console.log("Email:", email.value);
  console.log("Password:", password.value);
  const randomText = Math.random().toString(36).substring(2, 15);
  localStorage.setItem("loginStatus", randomText);
  router.push("/dashboard");
}
</script>

<style scoped></style>
