<template>
  <div class="post-container py-8">
    <h3 class="text-3xl font-bold">
      <NuxtLink :to="`/posts/`+post.id">{{post.title}}</NuxtLink>
    </h3>
    <div class="post-meta text-gray-700 flex items-center space-x-2">
      <div> Feb, 2002</div>
      <div>&middot;</div>
      <div>{{ post.user.name }}</div>
    </div>
    <div class="post-preview leading-relaxed mt-4">
      {{post.body}}
    </div>
    <div class="mt-4">
      <NuxtLink :to="`/posts/`+post.id" class="bg-blue-700 hover:bg-blue-800 text-white rounded inline-block px-4 py-2">Read more</NuxtLink>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'
defineProps({
  post: Object
})
</script>