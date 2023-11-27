<script setup lang="ts">
useHead({
  title: 'Create Destination - Dashboard',
})
const store = (() => {
  console.log(null)
})
const form = reactive({
  errors: {
    code: String,
    location: String,
    desc: String,
  },
  code: String,
  location: String,
  desc: String,
})
</script>
<template>
  <NuxtLayout name="auth">
    <div class="max-w-4xl bg-white rounded-md shadow overflow-hidden">
      <form @submit.prevent="store">
        <div class="flex flex-wrap p-8 text-neutral-700">
          <text-input v-model="form.code" :error="form.errors.code" class="pb-8 pr-6 w-full lg:w-1/2" label="Code" />
          <text-input v-model="form.location" :error="form.errors.location" class="pb-8 pr-6 w-full lg:w-1/2"
            label="Location" />
          <textarea-input v-model="form.desc" :error="form.errors.desc" class="pb-8 pr-6 w-full lg:w-1/2"
            label="Description" />
        </div>
        <div class="flex items-center justify-end px-8 py-4 bg-gray-50 border-t border-gray-100">
          <button class="py-2 px-5 bg-purple-500 hover:bg-violet-500 rounded-lg font-semibold">Create Destination</button>
        </div>
      </form>
    </div>
  </NuxtLayout>
</template>
