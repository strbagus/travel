<script setup lang="ts">
import { ref, onMounted } from 'vue'
onMounted(() => {
    if(window.screen.width >=480){
      navToggle.value = true
    }
})
const props = defineProps({
  name: String,
})
const navToggle = ref(false)
const navClick = (() => {
  navToggle.value = navToggle.value ? false : true
})
console.log(props.name)
</script>
<template>
  <nav class="sticky z-40 top-0 bg-neutral-900 py-4">
    <div class="max-w-[1000px] mx-auto flex justify-between items-center flex-col md:flex-row">
      <div class="w-full flex justify-between items-center px-4 md:px-0">
        <NuxtLink to="/" class="text-white text-xl font-medium italic">Travel Jogja</NuxtLink>
        <div class="text-white cursor-pointer block md:hidden" @click="navClick">
          <Icon name="hamburger" :size="32"/>
        </div>
      </div>
      <div class="w-full md:w-auto text-center mt-3 md:mt-0 duration-500" v-if="navToggle">
        <ul class="text-white flex flex-col md:flex-row border-t md:border-none px-12 md:px-0">
          <li :class="props.name==='home' ? 'border-b border-purple-500' : ''" class="px-4 hover:text-neutral-200 mt-5 mb-1 md:mt-1"><NuxtLink to="/">Home</NuxtLink></li>
          <li :class="props.name==='tour' ? 'border-b border-purple-500' : ''" class="px-4 hover:text-neutral-200 my-1"><NuxtLink to="/tour">Tour</NuxtLink></li>
          <li :class="props.name==='destination' ? 'border-b border-purple-500' : ''" class="px-4 hover:text-neutral-200 mt-1 mb-5 md:mb-1"><NuxtLink to="/destination">Destination</NuxtLink></li>
        </ul>
      </div>
    </div>
  </nav>
</template>
