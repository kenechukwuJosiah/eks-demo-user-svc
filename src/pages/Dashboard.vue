<template>
  <div class="flex min-h-screen w-screen bg-purple-50 text-purple-900">
    <!-- Sidebar -->
    <aside class="w-60 bg-white p-5 shadow-md">
      <div class="mb-10">
        <h2 class="text-xl font-bold text-purple-700">User Dashboard</h2>
      </div>

      <nav class="space-y-3">
        <a
          href="#"
          class="block px-3 py-2 rounded bg-purple-100 text-purple-700 font-medium"
          >🏠 Dashboard</a
        >
        <a
          href="#"
          class="block px-3 py-2 rounded hover:bg-purple-100 font-medium"
          >👤 Profile</a
        >
        <a
          href="#"
          class="block px-3 py-2 rounded hover:bg-purple-100 font-medium"
          >🔒 Security</a
        >
        <a
          href="#"
          class="block px-3 py-2 rounded hover:bg-purple-100 font-medium"
          >⚙️ Settings</a
        >
      </nav>

      <div class="mt-10">
        <button
          class="w-full bg-purple-700 text-white py-2 rounded hover:bg-purple-800 text-sm"
        >
          Log Out
        </button>
      </div>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 p-6">
      <!-- Top Header -->
      <div class="flex justify-between items-center mb-6">
        <h1 class="text-2xl font-bold">Welcome, {{ user.name }}!</h1>
        <div class="text-sm text-purple-500">Today: {{ currentDate }}</div>
      </div>

      <!-- Info Cards -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
        <div
          class="bg-white p-4 rounded-lg shadow-md border-l-4 border-purple-400"
        >
          <p class="text-purple-500 text-sm mb-1">Email</p>
          <p class="text-lg font-bold break-all">{{ user.email }}</p>
        </div>
        <div
          class="bg-white p-4 rounded-lg shadow-md border-l-4 border-purple-400"
        >
          <p class="text-purple-500 text-sm mb-1">Account Created</p>
          <p class="text-lg font-bold">{{ user.createdAt }}</p>
        </div>
        <div
          class="bg-white p-4 rounded-lg shadow-md border-l-4 border-purple-400"
        >
          <p class="text-purple-500 text-sm mb-1">Status</p>
          <p class="text-lg font-bold">
            <span :class="user.active ? 'text-green-600' : 'text-red-600'">{{
              user.active ? "Active" : "Inactive"
            }}</span>
          </p>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

onMounted(() => {
  const loginStatus = localStorage.getItem("loginStatus");
  if (!loginStatus) {
    router.push("/login");
  }
});

const currentDate = new Date().toLocaleDateString(undefined, {
  weekday: "long",
  month: "short",
  day: "numeric",
  year: "numeric",
});

// Example user data; replace with real user info as needed
const user = ref({
  name: "Justin",
  email: "justin@example.com",
  createdAt: "2023-01-15",
  active: true,
});
</script>

<style scoped>
body {
  font-family: "Inter", sans-serif;
}
</style>
