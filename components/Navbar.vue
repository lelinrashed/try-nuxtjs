<template>
  <div class="flex justify-between">
    <div class="flex">
      <NuxtLink class="mr-1" to="/">Home</NuxtLink> |
      <NuxtLink class="mx-1" to="/iphone">iPhone</NuxtLink> |
      <div class="ms-1">
        Cart ({{ cart.length }})
      </div>
    </div>
    <div v-if="auth.isAuthenticated">
      <NuxtLink class="mr-1" to="/profile">Profile</NuxtLink> |
      <button class="ms-1" @click="logout">Logout</button>
    </div>
    <NuxtLink v-else to="/login">Login</NuxtLink>
  </div>
</template>

<script setup>
const cart = useCart();
const auth = useAuth();

function logout() {
  auth.value.isAuthenticated = false;
}
</script>