<template>
  <div>
    <HomeWelcome />
    <button @click="toggleComponent">Toggle</button>
    <component :is="myComponent" />
  </div>
  <NuxtPage />
</template>

<script setup>
const myComponent = shallowRef(resolveComponent('Counter'))

function toggleComponent() {
  myComponent.value = resolveComponent('HomeWelcome')
}
</script>
