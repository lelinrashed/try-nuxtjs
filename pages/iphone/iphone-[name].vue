<template>
  <div>
    <br>
    <h1>iPhone {{ name }}</h1>
    <br>
    <img class="w-64" src="/images/iphone-15.webp" alt="iPhone 15">
    <br>
    <button @click="addToCart" class="bg-slate-600 text-white px-6 py-1 rounded-sm">
      <span v-if="!inCart">Buy now</span>
      <span v-else>Remove from the cart</span>
    </button>
  </div>
</template>

<script setup>
// define page metadata
definePageMeta({
  layout: 'default'
})

// use the cart composable
const cart = useCart();

// use the route composable
const route = useRoute();

// make the slug readable
const name = computed(() => {
  return route.params.name.replaceAll('-', ' ');
});

// get the fullname of the phone
const fullname = computed(() => {
  return `iPhone-${route.params.name}`;
});

// use the head composable
useHead({
  title: `iPhone ${route.params.name}`,
  meta: [
    {
      hid: 'description',
      name: 'description',
      content: 'iPhone 15'
    }
  ]
})

// get the fullname of the phone
const inCart = computed(() => {
  return cart.value.find((item) => item.name === fullname.value);
});

// add the phone to the cart
function addToCart() {
  if (!inCart.value) {
    cart.value.push({
      name: fullname.value,
    });
  } else {
    cart.value = cart.value.filter((item) => item.name !== fullname.value);
  }
}
</script>