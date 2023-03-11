<template>
  <Title>{{title}}</Title>
  <div class="bg-gray-100 min-h-screen min-w-full text-gray-900">
    <nav class="bg-white shadow text-lg-px-6 py-6">
      <div class="container mx-auto flex items-center justify-between">
        <div>
          <NuxtLink to="/">Logo</NuxtLink>
        </div>
        <div>
          <ul class="flex space-x-12">
            <li><NuxtLink to="/">Home</NuxtLink></li>
            <li><NuxtLink to="/about">About</NuxtLink></li>
            <li><NuxtLink to="/register">Register</NuxtLink></li>
            <li><NuxtLink to="/login">Login</NuxtLink></li>
            <li><NuxtLink to="/contact">Contact</NuxtLink></li>
          </ul>
        </div>
      </div>
    </nav>
    <slot></slot>
  </div>
</template>
<script setup>
const title = useState('title', () => 'Nuxt 3 Blog')
</script>
<script>
export default {
  name: "default"
}
</script>
<style>
.router-link-active {
  @apply font-bold;
}
</style>
