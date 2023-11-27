<script setup lang="ts">
import { onMounted, ref } from 'vue'
const breadcrumbs = ref<Array<Breadcrumb>>([])
const route = useRoute()
onMounted(() => {
  const full = route.path
  const arrs = full.split('/')
  for (let i = 1; i < arrs.length; i++) {
    let links = []
    for (let j = 1; j <= i; j++) {
      links.push(arrs[j])
    }
    breadcrumbs.value.push({
      title: arrs[i],
      link: `/${links.join('/')}`,
    })
  }
})
interface Breadcrumb {
  title: string;
  link: string;
}
</script>
<template>
  <div class="flex bg-gradient-to-br from-violet-100 to-zinc-100">
    <div class="w-[280px] sticky top-0 bg-violet-600 from-violet-600 to-purple-600 h-screen px-6 py-4">
      <div class="text-violet-100 flex items-center">
        <Icon name="location-multi" :size="64" />
        <span class="ml-2 text-2xl font-medium">TravelJogja</span>
      </div>
      <div class="text-white text-lg my-8">
        <SideNavLink title="Dashboard" link="/dashboard" icon="home" />
        <SideNavLink title="Destinations" link="/dashboard/destinations" icon="location" />
        <!-- <SideNavLink title="Tours" link="/dashboard/tours" icon="location-multi" /> -->
      </div>
    </div>
    <div class="grow text-neutral-100">
      <div class="w-full bg-neutral-800 py-3 px-10 flex justify-between items-center sticky top-0">
        <div class="flex items-center capitalize">
          <template v-for="(b, index ) in breadcrumbs">
            <Icon v-if="index !== 0" name="right" :size="24" />
            <NuxtLink v-if="b.link !== route.path" :to="b.link"
              class="font-medium text-violet-100 hover:text-violet-300 flex items-center">
              <Icon v-if="index == 0" name="home" :size="20" class="mr-1" />
              <span>{{ b.title }}</span>
            </NuxtLink>
            <template v-else>
              <Icon v-if="index == 0" name="home" :size="20" class="mr-1" />
              <span class="text-violet-100">{{ b.title }}</span>
            </template>
          </template>
        </div>
        <div>
          <Dropdown align="right" width="48">
            <template #trigger>
              <span class="inline-flex rounded-md">
                <button type="button"
                  class="inline-flex items-center px-3 py-1 border border-transparent text-sm leading-4 font-medium rounded-md text-gray-800 bg-white hover:text-black focus:outline-none transition ease-in-out duration-150">
                  John Doe 
                  <Icon name="down" :size="16" />
                </button>
              </span>
            </template>
            <template #content>
              <!-- <DropdownLink href="/dashboard"> Profile </DropdownLink> -->
              <DropdownLink href="/login" method="post" as="button">
                Log Out
              </DropdownLink>
            </template>
          </Dropdown>
        </div>
      </div>
      <div class="max-w-5xl py-5 md:pl-8">
        <slot />
      </div>
    </div>
  </div>
</template>
