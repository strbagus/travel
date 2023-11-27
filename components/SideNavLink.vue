<script setup lang="ts">
const props = defineProps({
  title: String,
  link: String,
  icon: String,
})
const route = useRoute()
  
</script>
<template>
  <NuxtLink :to="props.link" class="border-l-4 pl-1 hover:border-neutral-100 flex gap-2 duration-100 items-center hover:text-violet-100 my-2" :class="route.path==props.link ? 'border-neutral-100 text-violet-100 font-medium' : 'border-transparent'">
    <Icon :name="props.icon" :size="24" />
    <span>{{ props.title }}</span>
  </NuxtLink>
</template>
