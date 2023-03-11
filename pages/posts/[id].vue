<template>
  <div class="container mx-auto w-1/2 py-8">
    <h3 class="text-3xl font-bold">
      <NuxtLink :to="`/posts/${post.id}`">{{ post.title }}</NuxtLink>
    </h3>
    <div class="post-meta text-gray-700 flex items-center space-x-2">
      <div> Feb, 2002</div>
      <div>&middot;</div>
      <div>{{ post.user.name }}</div>
    </div>
    <div class="post-preview mt-4">
      ID: {{id}}
      {{post.body}}
    </div>
  </div>
</template>

<style>
.router-link-active {
  @apply font-bold;
}
</style>

<script setup>
const route = useRoute();
const id = route.params.id;
const {data: post} = await useFetch('http://localhost/api/posts/'+id);
</script>

