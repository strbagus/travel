<script setup lang="ts">
import { defineComponent, onMounted, computed, ref } from 'vue'

import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination, Autoplay } from 'swiper'
import 'swiper/css'
import 'swiper/css/pagination'
import 'swiper/css/autoplay'

defineComponent({
  Swiper,
  SwiperSlide,
})
const modules: any = [ Pagination, Autoplay ]
onMounted(() => {
    smallDevice.value = window.screen.width < 480 ? true : false
})
const arrayChunks = ((items: Array<any>, chunkSize: number) => {
  const chunks: Array<any> = []
  let index = 0
  while(index < items.length) {
    chunks.push(items.slice(index, index + chunkSize))
    index += chunkSize
  }
  return chunks
})
const chunkReviews = computed(() => {
  return arrayChunks(reviews, 2)
})
const smallDevice = ref<Boolean>()
const chunkAgents = computed(() => {
  let size = smallDevice.value ? 1 : 3
  return arrayChunks(reviews, size)
})
const loremIp: string = "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nam consequuntur hic temporibus alias laboriosam natus non. Nisi molestiae, vitae, magni, voluptatum ex eveniet maxime earum et fuga nostrum provident beatae."
const reviews: Array<reviewsItem> = [
  { image: "avatar1.jpg", rating: 4, note: loremIp, name: "Alex" },
  { image: "avatar2.jpg", rating: 5, note: loremIp, name: "George" },
  { image: "avatar3.jpg", rating: 5, note: loremIp, name: "Sandy" },
  { image: "avatar4.jpg", rating: 4, note: loremIp, name: "Sena" },
  { image: "avatar5.jpg", rating: 5, note: loremIp, name: "John" },
  { image: "avatar6.jpg", rating: 5, note: loremIp, name: "Brian" },
]
interface reviewsItem {
  image: string,
  name: string,
  rating: number,
  note: string,
}
</script>
<template>
  <NuxtLayout name="main">
    <header class="h-screen bg-blue-500 relative w-full flex items-center">
      <img src="assets/banner.webp" class="absolute h-full w-full top-0 left-0 object-cover">
      <div class="absolute h-full w-full bg-black opacity-40" />
      <div class="relative w-full max-w-[1200px] mx-auto px-5">
        <div class="w-full md:w-1/2"> 
          <h1 class="text-4xl md:text-7xl text-white uppercase font-medium">plan the perfect trip in yogyakarta!</h1>
          <p class="text-sm md:text-lg text-white italic">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis error, odit dolorem atque animi tenetur fugit.</p>
        </div>
      </div>
      <div class="absolute bottom-0 w-full flex justify-center">
        <div class="pb-10 text-neutral-200 bouncing"> 
          <Icon name="doubleTop" :size="48"/>
        </div>
      </div>
    </header>
    <NavBar name="home" />
    <div class="min-h-screen bg-cyan-900">
      <div class="max-w-[1000px] mx-auto px-3">
        <h2>What we Provided</h2>
        <div class="flex flex-wrap">
          <div class="w-full md:w-1/2 bg-red-500">
          </div>
          <div class="w-full md:w-1/2 p-3">
            <div class="w-full my-4 bg-neutral-50 px-5 py-3 rounded-xl shadow flex justify-between items-center">
              <div class="text-xl font-medium">Rentals</div>
              <a href="/rental"><Icon name="right" :size="32"/></a>
            </div>
            <div class="w-full my-4 bg-neutral-50 px-5 py-3 rounded-xl shadow flex justify-between items-center">
              <div class="text-xl font-medium">Rentals</div>
              <a href="/rental"><Icon name="right" :size="32"/></a>
            </div>
            <div class="w-full my-4 bg-neutral-50 px-5 py-3 rounded-xl shadow flex justify-between items-center">
              <div class="text-xl font-medium">Rentals</div>
              <a href="/rental"><Icon name="right" :size="32"/></a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="bg-gradient-to-r from-cyan-500 to-cyan-600 py-24">
      <div class="max-w-[1000px] mx-auto">
        <h2 class="text-center text-white text-3xl font-medium">Our Client Stories</h2>
        <swiper
          :modules="modules"
          :slides-per-view="1"
          :space-between="10"
          autoplay
          :pagination="{ clickable: false }"
          class="flex flex-wrap justify-evenly mt-5"
        >
          <swiper-slide v-for="(views, index) in chunkReviews" class="flex-wrap py-8" :key="index">
            <div v-for="review in views" class="px-4 py-2 w-full md:w-1/2">
              <div class="bg-cyan-800 rounded-xl px-10 py-4">
                <div class="flex justify-between flex-col md:flex-row items-center">
                  <div class="flex items-center">
                    <img :src="`assets/${review.image}`" :alt="review.name" loading="lazy" class="rounded-full w-16">
                    <div class="text-xl text-white font-semibold ml-5">{{ review.name }}</div>
                  </div>
                  <div class="flex items-center text-yellow-500">
                    <Icon v-for="_ in 5" name="star" :size="32"/>
                  </div>
                </div>
                <p class="my-3 text-sm text-white">{{ review.note }}</p>
              </div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </div>
    <div class="bg-cyan-50 py-24">
      <div class="max-w-[1000px] mx-auto">
        <h2 class="text-center text-cyan-900 text-3xl font-medium">Contact our Agents</h2>
        <swiper
          :modules="modules"
          :slides-per-view="1"
          :space-between="10"
          autoplay
          :pagination="{ clickable: false }"
          class="flex flex-wrap justify-evenly mt-5"
        >
          <swiper-slide v-for="(views, index) in chunkAgents" class="pb-8 flex-wrap" :key="index">
            <div v-for="review in views" class="px-4 py-2 w-full md:w-1/3">
              <div class="bg-cyan-800 rounded-xl px-10 py-4">
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
    </div>
  </NuxtLayout>
</template>
<style scoped>
.bouncing {
  animation: bounce 2.75s infinite;
}
@keyframes bounce {
  0%       { margin-bottom:0; }
  20%, 50% { margin-bottom:20px; }
  35% { margin-bottom: 10px; }
  75%     { margin-bottom:0; }
}
.swiper-slide, swiper-slide {
  display: flex !important;
}
</style>
