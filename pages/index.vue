<script setup lang="ts">
import { defineComponent, onMounted, computed, ref } from 'vue'

import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination, Autoplay } from 'swiper'
import 'swiper/css'
import 'swiper/css/pagination'
import 'swiper/css/autoplay'

useHead({
  title: 'Travel Jogja',
  meta: [
    { name: 'title', content: 'Travel Jogja Portfolio Strbagus.' },
    { name: 'description', content: 'Plan the Perfect Trip on Yogyakarta with wonderfull tour package with many Great Destination!' },
    { name: 'keywords', content: 'Portofolio Satrio Bagus, Strbagus, Travel Jogja' },
    { name: 'author', content: 'strbagus' },
    { name: 'tag', content: 'Portoflio Website' },
    { name: 'og:title', content: 'Travel Jogja Portfolio Strbagus.' },
    { name: 'og:image', content: 'https://travel.strbagus.com/assets/dummy-md.jpg' },
    { name: 'og:description', content: 'Plan the Perfect Trip on Yogyakarta with wonderfull tour package with many Great Destination!' },
    { name: 'og:url', content: 'https://travel.strbagus.com' },
    { name: 'twitter:title', content: 'Travel Jogja Portfolio Strbagus.' },
    { name: 'twitter:image', content: 'https://travel.strbagus.com/assets/dummy-md.jpg' },
    { name: 'twitter:description', content: 'Plan the Perfect Trip on Yogyakarta with wonderfull tour package with many Great Destination!' },
    { name: 'twitter:url', content: 'https://travel.strbagus.com' },
  ],
})

defineComponent({
  Swiper,
  SwiperSlide,
})
const modules: any = [Pagination, Autoplay]
onMounted(() => {
  smallDevice.value = window.screen.width < 480 ? true : false
})
const arrayChunks = ((items: Array<any>, chunkSize: number) => {
  const chunks: Array<any> = []
  let index = 0
  while (index < items.length) {
    chunks.push(items.slice(index, index + chunkSize))
    index += chunkSize
  }
  return chunks
})
const smallDevice = ref<Boolean>()
const chunkAgents = computed(() => {
  let size = smallDevice.value ? 1 : 3
  return arrayChunks(reviews, size)
})
const loremIp: string = "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nam consequuntur hic temporibus alias laboriosam natus non. Nisi molestiae, vitae, magni, voluptatum ex eveniet maxime earum et fuga nostrum provident beatae."
const reviews: Array<reviewsItem> = [
  { image: "avatar1.jpg", note: loremIp, name: "Alex" },
  { image: "avatar2.jpg", note: loremIp, name: "George" },
  { image: "avatar3.jpg", note: loremIp, name: "Sandy" },
  { image: "avatar4.jpg", note: loremIp, name: "Sena" },
  { image: "avatar5.jpg", note: loremIp, name: "John" },
  { image: "avatar6.jpg", note: loremIp, name: "Brian" },
]
interface reviewsItem {
  image: string,
  name: string,
  note: string,
}
</script>
<template>
  <NuxtLayout name="main">
    <header class="h-screen bg-neutral-200 relative w-full flex items-center">
      <img src="/assets/banner.webp" alt="Travel Jogja Home Banner" class="absolute h-full w-full top-0 left-0 object-cover">
      <div class="absolute h-full w-full bg-black opacity-40" />
      <div class="relative w-full max-w-[1200px] mx-auto px-5">
        <div class="w-full md:w-1/2">
          <h1 class="text-4xl md:text-7xl text-white uppercase font-medium">plan the perfect trip in Yogyakarta!</h1>
          <p class="text-sm md:text-lg text-white italic">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis
            error, odit dolorem atque animi tenetur fugit.</p>
        </div>
      </div>
      <div class="absolute bottom-0 w-full flex justify-center">
        <div class="pb-10 text-neutral-200 bouncing">
          <Icon name="doubleTop" :size="48" />
        </div>
      </div>
    </header>
    <NavBar name="home" />
    <div class="max-w-[1000px] mx-auto px-3 py-12">
      <h2 class="text-center text-purple-700 text-3xl font-medium">Recomended Destination</h2>
      <swiper :modules="modules" :slides-per-view="1" :space-between="10" autoplay :pagination="{ clickable: false }"
        class="flex flex-wrap justify-evenly mt-5">
        <swiper-slide v-for="(views, index) in chunkAgents" class="pb-8 flex-wrap" :key="index">
          <div v-for="view in views" class="px-4 py-2 w-full md:w-1/3 group">
            <NuxtLink :to="`/destination/destination-${view.name}`">
              <div class="relative w-full aspect-[3/4]">
                <img src="/assets/dummy-md.jpg" alt="Image Description" loading="lazy"
                  class="absolute rounded-tr-xl rounded-b-xl object-cover h-full w-full left-0 right-0">
                <div class="opacity-90 h-full text-white flex flex-col justify-end">
                  <div class="bg-black bg-opacity-0 group-hover:bg-opacity-10 rounded-tr-xl h-full duration-200"></div>
                  <div
                    class="px-5 pb-4 pt-2 flex justify-between bg-black bg-opacity-50 group-hover:bg-opacity-80 rounded-b-xl duration-200">
                    <div>
                      <div class="text-lg font-medium">Destination {{ view.name }}</div>
                      <div class="flex items-center">
                        <Icon name="location" :size="18" />
                        <span class="text-xs">Water Castle, Kraton, Yogyakarta</span>
                      </div>
                    </div>
                    <div class="flex items-center">
                      <Icon name="star" :size="20" class="text-amber-400" />
                      <span class="font-medium">4</span>
                    </div>
                  </div>
                </div>
              </div>
            </NuxtLink>
          </div>
        </swiper-slide>
      </swiper>
    </div>
    <div class="py-12 px-3 md:px-0">
      <h2 class="text-center text-purple-700 text-3xl font-medium mb-3">Featured Tour Package</h2>
      <div class="flex flex-wrap max-w-[800px] mx-auto bg-purple-200 rounded-r-lg">
        <div class="w-full md:w-1/2">
          <Image src="/assets/dummy-md.jpg" alt="Image Description" loading="lazy" class="aspect-[3/2] md:aspect-[1/1]" />
        </div>
        <div class="w-full md:w-1/2 px-5 flex flex-col justify-center my-2">
          <h2 class="text-2xl text-purple-700 font-medium group-hover:text-purple-800">Tour Package Name</h2>
          <div class="flex items-center">
            <Icon name="star" :size="20" class="text-amber-400" />
            <div class="font-semibold text-neutral-700">&nbsp;5</div>
          </div>
          <ul class="list-disc pl-6 text-neutral-700 group-hover:text-neutral-700 hidden md:block my-3">
            <li v-for="i in 5" class="py-1 hover:text-purple-700">
              <NuxtLink :to="`/destination/destination-name-${i}`">
                Destination Name {{ i }}
              </NuxtLink>
            </li>
          </ul>
          <div class="flex justify-center">
            <NuxtLink to="/tour/tour-name-1">
              <div class="py-2 px-5 text-white bg-purple-600 font-medium hover:bg-purple-700 rounded-lg">
                Rp. 599,000
              </div>
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
    <div class="py-12 max-w-[1000px] mx-auto">
      <h2 class="text-center text-purple-700 text-3xl font-medium">Contact our Agents</h2>
      <swiper :modules="modules" :slides-per-view="1" :space-between="10" autoplay :pagination="{ clickable: false }"
        class="flex flex-wrap justify-evenly mt-5">
        <swiper-slide v-for="(views, index) in chunkAgents" class="pb-8 flex-wrap" :key="index">
          <div v-for="review in views" class="px-4 py-2 w-full md:w-1/3">
            <div class="bg-gradient-to-tr from-violet-500 to-purple-400 rounded-xl px-10 py-4">
              <div class="flex flex-col justify-between items-center">
                <img :src="`assets/${review.image}`" :alt="review.name" loading="lazy" class="rounded-full w-32">
                <div class="text-xl text-white font-semibold">{{ review.name }}</div>
              </div>
              <p class="my-3 text-sm text-white text-center">{{ review.note }}</p>
            </div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </NuxtLayout>
</template>
<style scoped>
.bouncing {
  animation: bounce 2.75s infinite;
}

@keyframes bounce {
  0% {
    margin-bottom: 0;
  }

  20%,
  50% {
    margin-bottom: 20px;
  }

  35% {
    margin-bottom: 10px;
  }

  75% {
    margin-bottom: 0;
  }
}

.swiper-slide,
swiper-slide {
  display: flex !important;
}
</style>
