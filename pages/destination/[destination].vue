<script setup lang="ts">
const route = useRoute()
useHead({
  title: `${ route.params.destination } - Travel Jogja`,
  meta: [
    { name: 'title', content: 'List Destinations - Travel Jogja Portfolio Strbagus.' },
    { name: 'description', content: 'Plan the Perfect Trip on Yogyakarta with wonderfull tour package with many Great Destination!' },
  ],
})
</script>
<template>
  <NuxtLayout name="main">
    <NavBar name="destination" />
    <div class="max-w-[1080px] mx-auto pt-6 pb-12 px-3 md:px-0">
      <div class="flex flex-wrap">
        <div class="w-full md:w-2/3 px-3">
          <div class="aspect-[3/2] bg-neutral-300 w-full relative">
            <img src="/assets/dummy-md.jpg" class="absolute h-full w-full object-cover left-0 right-0">
          </div>
          <h1 class="text-3xl font-medium mt-2 text-neutral-800">{{ route.params.destination}}</h1>
          <Rating :rating="4" />
          <p class="py-3 my-2 border-y-2 border-neutral-300 text-neutral-700">
            Lorem ipsum dolor sit amet, officia excepteur ex fugiat reprehenderit enim labore culpa sint ad nisi Lorem pariatur mollit ex esse exercitation amet. Nisi anim cupidatat excepteur officia. Reprehenderit nostrud nostrud ipsum Lorem est aliquip amet voluptate voluptate dolor minim nulla est proident. Nostrud officia pariatur ut officia. Sit irure elit esse ea nulla sunt ex occaecat reprehenderit commodo officia dolor Lorem duis laboris cupidatat officia voluptate. Culpa proident adipisicing id nulla nisi laboris ex in Lorem sunt duis officia eiusmod. Aliqua reprehenderit commodo ex non excepteur duis sunt velit enim. Voluptate laboris sint cupidatat ullamco ut ea consectetur et est culpa et culpa duis.
          </p>
          <ul class="flex flex-wrap text-neutral-600 my-4">
            <li v-for="i in 5" class="bg-purple-300 py-1 px-2 text-sm mx-1 my-1 rounded">#&nbsp; Tag{{ i }}</li>
          </ul>
          <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d63245.97085556032!2d110.33364492822413!3d-7.803248457439516!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e7a5787bd5b6bc5%3A0x21723fd4d3684f71!2sYogyakarta%2C%20Yogyakarta%20City%2C%20Special%20Region%20of%20Yogyakarta!5e0!3m2!1sen!2sid!4v1700858947294!5m2!1sen!2sid" style="border:0;" allowfullscreen="true" loading="lazy" referrerpolicy="no-referrer-when-downgrade" class="w-full aspect-[5/2]"></iframe>
        </div>
        <div class="w-full md:w-1/3 border-l-2 border-neutral-300 px-3">
          <div class="sticky top-20">
            <h2 class="text-xl font-medium text-neutral-800">Other Destination</h2>
            <div class="flex flex-col">
              <template v-for="i in 6">
                <NuxtLink :to="`/destination/destination-name-${i}`">
                  <div class="flex py-2 group border-b-2 border-neutral-300 hover:border-purple-300 items-center">
                    <div class="w-1/3">
                      <Image src="/assets/dummy-xs.jpg" class="aspect-[3/2]" />
                    </div>
                    <div class="w-2/3 px-2 flex flex-col justify-between">
                      <h3 class="text-xl font-medium text-purple-600 group-hover:text-purple-700">Destination Name {{ i }}</h3>
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
