<script setup lang="ts">
  const route = useRoute()
useHead({
  title: 'Dashboard',
})
</script>
<template>
  <NuxtLayout name="auth">
    <h1 class="text-3xl text-black">{{ route.path }}</h1>
  </NuxtLayout>
</template>
