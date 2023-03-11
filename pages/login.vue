<template>
  <div class="mt-8 sm:mx-auto sm:w-full sm:max-w-md">
    <div class="bg-white py-8 px-4 shadow sm:rounded-lg sm:px-10">
      <form class="space-y-6" action="#" method="POST" @submit.prevent="login">
        <div>
          <label for="email" class="block text-sm font-medium leading-6 text-gray-900">Email address</label>
          <div class="mt-2">
            <input id="email" v-model="email" name="email" type="email" autocomplete="email" required="" class="block w-full rounded-md border-0 p-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
          </div>
        </div>

        <div>
          <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Password</label>
          <div class="mt-2">
            <input id="password" v-model="password" name="password" type="password" autocomplete="current-password" required="" class="block w-full rounded-md border-0 p-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
          </div>
        </div>
        <ul v-if="errors.length > 0">
          <li v-for="(error,index) in errors"> {{error}} </li>
        </ul>
        <div>
          <button type="submit" class="w-full align-center rounded-full bg-indigo-600 py-2 px-3 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Login</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import Cookies from 'js-cookie'
const email = ref('')
const password = ref('')
let errors = ref([])
async function login() {
  await fetch('http://localhost/sanctum/csrf-cookie', {
    credentials: "include",
    headers: {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }
  })
  try {
    await useFetch('http://localhost/login', {
      method: 'POST',
      credentials: "include",
      headers: {
        'Content-Type': 'application/json',
        'Accept': 'application/json',
        'X-XSRF-TOKEN': useCookie('XSRF-TOKEN').value
      },
      body: {
        email: email.value,
        password: password.value
      },
      onRequestError({ request, options, error }) {
        console.log(error)
      },
    })
  } catch(err) {
    console.log('erro')
    console.log(err)
  }
}
</script>