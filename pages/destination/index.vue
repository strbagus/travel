<script setup lang="ts">
useHead({
  title: 'Destinations - Travel Jogja',
  meta: [
    { name: 'title', content: 'List Destinations - Travel Jogja Portfolio Strbagus.' },
    { name: 'description', content: 'Plan the Perfect Trip on Yogyakarta with wonderfull tour package with many Great Destination!' },
  ],
})
</script>
<template>
  <NuxtLayout name="main">
    <NavBar name="destination" />
    <div class="max-w-[1080px] mx-auto py-12 px-3 md:px-0">
      <h1 class="text-3xl font-semibold text-neutral-800">List Destination</h1>
      <div class="flex flex-wrap">
        <div class="w-full md:w-2/3 px-3 order-2 md:order-1">
          <NuxtLink v-for="i in 6" :to="`/destination/destination-name-${i}`">
            <div class="flex flex-wrap items-center border-b-4 hover:border-purple-300 py-4 group my-2">
              <div class="w-full md:w-1/3">
                <Image src="/assets/dummy-sm.jpg" class="aspect-[3/2]" />
              </div>
              <div class="w-full md:w-2/3 md:pl-3">
                <h2 class="text-xl mt-2 md:mt-0 font-medium text-purple-700 group-hover:text-purple-800">Destination Name {{ i }}</h2>
                <Rating :rating="5" class="group-hover:text-amber-400" />
                <p class="text-sm mt-2 text-neutral-800 group-hover:text-black">
                  Lorem ipsum dolor sit, amet consectetur adipisicing elit. Placeat cupiditate necessitatibus doloremque
                  odit facilis rerum laudantium totam ratione possimus repudiandae maiores quae ipsum molestiae, assumenda
                  modi velit cum perferendis iure!
                </p>
              </div>
            </div>
          </NuxtLink>
        </div>
        <div class="w-full md:w-1/3 px-3 md:border-l-2 border-neutral-300 order-1 md:order-2">
          <div class="md:sticky md:top-20">
            <h3 class="text-2xl font-medium text-neutral-800">Categories</h3>
            <ul class="mt-3 overflow-auto">
              <li
                class="text-lg my-2 font-medium flex justify-between items-center bg-purple-400 py-1 px-3 rounded-lg text-white cursor-pointer">
                <span>Beach</span>
                <span class="text-neutral-100 text-xs italic">Active</span>
              </li>
              <li
                class="text-lg my-2 font-medium bg-purple-300 hover:bg-purple-400 duration-200 py-1 px-3 rounded-lg text-white cursor-pointer"
                v-for="_ in 5">
                <span>Beach</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
</NuxtLayout></template>
