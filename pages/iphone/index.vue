<template>
  <div>
    <NuxtLink to="/iphone/iphone-15">
      <br>
      <h1>iPhone 15</h1>
      <img class="w-40" src="/images/iphone-15.webp" alt="iPhone 15">
    </NuxtLink>
    <NuxtLink to="/iphone/iphone-14">
      <br>
      <h1>iPhone 14</h1>
      <img class="w-40" src="/images/iphone-15.webp" alt="iPhone 15">
    </NuxtLink>
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'default'
})
useHead({
  title: 'iPhones',
  meta: [
    {
      hid: 'description',
      name: 'description',
      content: 'iPhones'
    }
  ]
})

const { data } = useFetch("/api/iphones")
console.log('data', data.value);
</script>