<template>
  <div>
    <br>

    <form @submit.prevent="onSubmit">
      <label for="email">Email</label>
      <br>
      <input v-model="formData.email" type="email" placeholder="Email"
        class="border-2 border-gray-300 p-2 rounded-md w-80">

      <label for="password">Password</label>
      <br>
      <input v-model="formData.password" type="password" placeholder="Password"
        class="border-2 border-gray-300 p-2 rounded-md w-80">
      <div v-if="_error">
        <p class="text-red-600 text-sm">{{ _error }}</p>
      </div>

      <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-5">
        <span v-if="isLoading">Loading...</span>
        <span v-else>Login</span>
      </button>
    </form>
  </div>
</template>

<script setup>
const isLoading = ref(false);
const auth = useAuth();
const _error = ref(null);

const formData = reactive({
  email: 'eve.holt@reqres.in',
  password: 'cityslicka'
})

const loginUrl = 'https://reqres.in/api/login';
async function onSubmit() {
  if (isLoading.value) return;

  isLoading.value = true;
  const { data, error } = await useFetch(loginUrl, {
    method: 'post',
    body: formData
  });
  isLoading.value = false;

  if (data.value) {
    auth.value.isAuthenticated = true;
  }

  if (error.value) {
    _error.value = error.value.data.error;
    return;
  }

  navigateTo("/iphone");
}
</script>