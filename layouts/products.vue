<template>
  <div>
    <header class="fixed shadow-sm bg-white sticky top-0">
      <nav class="container mx-auto p-4 flex justify-between">
        <NuxtLink to="/" class="font-bold">Merch</NuxtLink>
        <ul class="flex gap-4">
          <li><NuxtLink to="/about">About</NuxtLink></li>
          <li><NuxtLink to="/">Merch</NuxtLink></li>
          <li>
            <div v-if="auth.isAuthenticated">
              <NuxtLink to="/profile">Profile</NuxtLink>
              <button @click="logout" class="ml-4">Logout</button>
            </div>
            <NuxtLink v-else to="/login">Login</NuxtLink>
          </li>
          <li>
            <CartIcon @click="toggleCart" />
          </li>
        </ul>
      </nav>
    </header>
    <CartRoom
      v-if="isVisible"
      class="fixed bg-slate-200 w-1/2 h-full right-0"
    />
    <div class="p-4">
      <slot class="absolute" />
    </div>
    <footer class="container mx-auto p-4 flex justify-between border-t-2">
      <ul class="flex gap-4">
        <li><NuxtLink to="/about">About</NuxtLink></li>
        <li><NuxtLink to="/">Merch</NuxtLink></li>
      </ul>
    </footer>
  </div>
</template>
<script setup>
import CartRoom from "../components/CartRoom.vue";
let isVisible = false;
function toggleCart() {
  isVisible = !isVisible;
}
const auth = useAuth();
function logout() {
  auth.value.isAuthenticated = false;
}
</script>
<style scoped>
.router-link-exact-active {
  color: #12b488;
}
</style>
