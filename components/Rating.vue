<script setup lang="ts">
import { defineProps } from 'vue';
const props = defineProps ({
  rating: Number,
  class: String,
})
</script>
<template>
  <div class="flex">
    <Icon v-for="_ in props.rating" name="star" :size="20" class="text-yellow-400" :class="class" />
    <Icon v-for="_ in 5-props.rating" name="star" :size="20" class="text-neutral-500" />
  </div>
</template>
