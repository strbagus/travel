<script setup lang="ts">
const props = defineProps({
  class: String,
  src: String,
  alt: String,
  loading: String,
})
</script>
<template>
  <div class="relative w-full" :class="props.class">
    <img :src="props.src" :loading="props.loading" :alt="props.alt" class="absolute object-cover h-full w-full left-0 right-0">
    <div class="h-0 opacity-0 group-hover:h-full group-hover:opacity-10 bg-black"></div>
  </div>
</template>
