<script setup lang="ts">
useHead({
  title: 'Tours - Travel Jogja',
  meta: [
    { name: 'title', content: 'List Tours - Travel Jogja Portfolio Strbagus.' },
    { name: 'description', content: 'Plan the Perfect Trip on Yogyakarta with wonderfull tour package with many Great Destination!' },
  ],
})
</script>
<template>
  <NuxtLayout name="main">
    <NavBar name="tour" />
    <div class="max-w-[720px] mx-auto pt-6 pb-12">
      <h1 class="text-3xl text-neutral-700 font-bold px-3 mb-2">Tours</h1>
      <div class="flex flex-wrap">
        <div class="w-full px-3">
          <NuxtLink
            v-for="j in 5"
            :to="`/tour/tour-package-${j}`"
            class="flex flex-wrap py-3 border-b-4 group hover:border-purple-300">
            <div class="w-full md:w-1/2 relative">
              <Image src="/assets/dummy-md.jpg" alt="test" class="aspect-[3/2]" />
            </div>
            <div class="w-full md:w-1/2 md:pl-2 flex flex-col justify-between py-2">
              <h2 class="text-2xl text-purple-700 font-medium group-hover:text-purple-800">Tour Package Name {{ j }}</h2>
              <ul class="list-disc pl-6 text-neutral-700 group-hover:text-neutral-700 hidden md:block">
                <li v-for="i in 4">Destination Name {{ i }}</li>
                <li>more..</li>
              </ul>
              <div class="flex justify-between">
                <span class="font-semibold text-purple-800 text-2xl group-hover:text-purple-900">Rp. 550,000</span>
                <Rating :rating="5" class="group-hover:text-amber-400" />
              </div>
            </div>
          </NuxtLink>
        </div>
      </div>
    </div>
  </NuxtLayout>
</template>
