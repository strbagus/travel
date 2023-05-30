<script setup lang="ts">
import { ref, onMounted } from 'vue'
onMounted(() => {
    if(window.screen.width >=480){
      navToggle.value = true
    }
})
const navToggle = ref(false)
const navClick = (() => {
  navToggle.value = navToggle.value ? false : true
})
</script>
<template>
  <nav class="sticky z-40 top-0 bg-neutral-900 py-4">
    <div class="max-w-[1000px] mx-auto flex justify-between items-center flex-col md:flex-row">
      <div class="w-full flex justify-between items-center px-4 md:px-0">
        <NuxtLink to="/" class="text-white text-xl font-medium italic">Travel Jogja</NuxtLink>
        <div class="text-white cursor-pointer block md:hidden" @click="navClick">
          <Icon name="hamburger" size="32"/>
        </div>
      </div>
      <div class="w-full md:w-auto text-center mt-3 md:mt-0" v-if="navToggle">
        <ul class="text-white flex flex-col md:flex-row border-t md:border-none">
          <li class="px-4 hover:text-neutral-200 mt-5 mb-1 md:mt-1"><NuxtLink to="/">Home</NuxtLink></li>
          <li class="px-4 hover:text-neutral-200 my-1"><NuxtLink to="/rental">Rental</NuxtLink></li>
          <li class="px-4 hover:text-neutral-200 mt-1 mb-5 md:mb-1"><NuxtLink to="/tour">Tour</NuxtLink></li>
        </ul>
      </div>
    </div>
  </nav>
</template>
