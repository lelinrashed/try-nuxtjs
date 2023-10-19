<template>
  <div>
    <h1>Profile page</h1>
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'default',
  middleware: ["auth"]
})
</script>