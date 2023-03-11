<template>
  <div class="container mx-auto w-1/2 py-8 divide-y space-y-8 divide-gray-300">
    <PostItem v-for="post in posts" :post="post" :key="post.id" />
  </div>
</template>
<script setup>
  const {data: posts} = await useFetch('http://localhost/api/posts');
</script>