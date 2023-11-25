<script setup lang="ts">
const route = useRoute()
</script>
<template>
  <NuxtLayout name="main">
    <NavBar name="tour" />
    <div class="max-w-[1080px] mx-auto pt-6 pb-12 px-3 md:px-0">
      <div class="flex flex-wrap">
        <div class="w-full md:w-2/3 px-3">
          <div class="aspect-[3/2] bg-neutral-300 w-full relative">
            <img src="/assets/dummy-md.jpg" class="absolute h-full w-full object-cover left-0 right-0">
          </div>
          <h1 class="text-3xl font-medium mt-2 text-neutral-800">{{ route.params.tour}}</h1>
          <div class="flex items-center py-1 justify-between flex-wrap">
            <Rating :rating="5" />
            <span class="text-lg text-purple-700 font-medium">Rp. 550.000</span>
            <span>1 Day Tour</span>
          </div>
          <div class="py-3 border-y-2 border-neutral-300 text-neutral-700">
            <span class="text-xl font-medium text-neutral-800">Destinations:</span>
            <div class="flex flex-wrap pb-2">
              <NuxtLink 
                v-for="i in 5"
                :to="`/destination/destination-name-${i}`"
                class="w-full md:w-1/2 px-2">
                <div class="flex group border-b border-neutral-300 py-2 hover:border-purple-400">
                  <div class="w-1/4 bg-neutral-300">
                    <Image src="/assets/dummy-xs.jpg" class="aspect-[3/2]" />
                  </div>
                  <div class="px-3 flex-col flex justify-between">
                    <h2 class="text-lg text-purple-700 font-medium group-hover:text-purple-800">Destination Name {{ i }}</h2>
                    <Rating :rating="4" class="group-hover:text-amber-400" />
                  </div>
                </div>
              </NuxtLink>
            </div>
            <p>
              Lorem ipsum dolor sit amet, officia excepteur ex fugiat reprehenderit enim labore culpa sint ad nisi Lorem pariatur mollit ex esse exercitation amet. Nisi anim cupidatat excepteur officia. Reprehenderit nostrud nostrud ipsum Lorem est aliquip amet voluptate voluptate dolor minim nulla est proident. Nostrud officia pariatur ut officia. Sit irure elit esse ea nulla sunt ex occaecat reprehenderit commodo officia dolor Lorem duis laboris cupidatat officia voluptate. Culpa proident adipisicing id nulla nisi laboris ex in Lorem sunt duis officia eiusmod. Aliqua reprehenderit commodo ex non excepteur duis sunt velit enim. Voluptate laboris sint cupidatat ullamco ut ea consectetur et est culpa et culpa duis.
            </p>
          </div>
        </div>
        <div class="w-full md:w-1/3 border-l-2 md:border-neutral-300 px-3 mt-5 md:mt-0">
          <div class="sticky top-20">
            <h3 class="text-xl font-medium text-neutral-800">Other Tour</h3>
            <div class="flex flex-col">
              <template v-for="i in 6">
                <NuxtLink :to="`/tour/tour-name-${i}`">
                  <div class="flex py-2 group border-b-2 border-neutral-300 items-center hover:border-purple-400">
                    <div class="w-1/3">
                      <Image src="/assets/dummy-xs.jpg" class="aspect-[3/2]" />
                    </div>
                    <div class="w-2/3 px-2 flex flex-col justify-between">
                      <h3 class="text-xl font-medium text-purple-600 group-hover:text-purple-700">Tour Name {{ i }}</h3>
                      <Rating :rating="4" class="group-hover:text-amber-400" />
                    </div>
                  </div>
                </NuxtLink>
              </template>
            </div>
          </div>
        </div>
      </div>
    </div>
  </NuxtLayout>
</template>
