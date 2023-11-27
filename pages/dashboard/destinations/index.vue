<script setup lang="ts">
function toEdit(id: Number){
  return navigateTo(`/dashboard/destinations/${id}`)
}
useHead({
  title: 'Destinations - Dashboard',
})
</script>
<template>
  <NuxtLayout name="auth">
    <div class="flex justify-end pb-3">
      <NuxtLink to="/dashboard/destinations/create"
        class="bg-purple-600 hover:bg-violet-600 font-semibold py-2 px-5 rounded-lg">
        Create
      </NuxtLink>
    </div>
    <div class="bg-white rounded-md shadow overflow-x-auto w-full text-gray-700">
      <table class="w-full whitespace-wrap">
        <thead>
          <tr class="text-center font-bold">
            <th class="pb-3 pt-4 px-6 w-1/3">Name</th>
            <th class="pb-3 pt-4 px-6 w-1/2">Location</th>
            <th class="pb-3 pt-4 px-6 w-1/6" colspan="2">Rating</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="i in 10" :key="i"
            class="hover:bg-violet-50 focus-within:bg-violet-50 cursor-pointer"
            @click="toEdit(i)"
          >
            <td class="border-t px-6 py-3">
              Water Castle
            </td>
            <td class="border-t px-6 py-3">
              Kraton, Yogyakarta
            </td>
            <td class="border-t px-6 py-3 text-end">
              5
            </td>
            <td class="border-t w-px pl-4 py-3">
              <Icon name="right" :size="20" />
            </td>
          </tr>
          <tr>
            <td class="px-6 py-4 border-t" colspan="4">No areaprojects found.</td>
          </tr>
        </tbody>
      </table>
    </div>
  </NuxtLayout>
</template>
