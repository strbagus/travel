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
        <a href="/" class="text-white text-xl font-medium italic">Travel Jogja</a>
        <div class="text-white cursor-pointer block md:hidden" @click="navClick">
          <svg width="32" height="32" viewBox="0 0 16 16"><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M2.75 12.25h10.5m-10.5-4h10.5m-10.5-4h10.5"/></svg>
        </div>
      </div>
      <div class="w-full md:w-auto text-center mt-3 md:mt-0" v-if="navToggle">
        <ul class="text-white flex flex-col md:flex-row border-t md:border-none">
          <li class="px-4 hover:text-neutral-200 mt-5 mb-1 md:mt-1"><a href="/">Home</a></li>
          <li class="px-4 hover:text-neutral-200 my-1"><a href="/rental">Rental</a></li>
          <li class="px-4 hover:text-neutral-200 mt-1 mb-5 md:mb-1"><a href="/tour">Tour</a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>
