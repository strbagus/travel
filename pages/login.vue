<script setup lang="ts">
function login(){
  return navigateTo('/dashboard')
}
useHead({
  title: 'Login - Travel Jogja',
})
</script>
<template>
  <div class="min-h-screen w-full bg-violet-200 flex justify-center items-center">
    <div class="max-w-[500px] bg-white shadow px-10 py-5 rounded-xl">
      <h1 class="text-center text-2xl font-bold font-mono text-purple-500">Welcome Back!</h1>
      <div class="min-w-[360px] border-y-2 border-netural-200 my-2 py-5">
        <div class="my-3">
          <label for="email" class="block text-sm">Email</label>
          <input type="email" placeholder="ex. example@email.com"
            class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400 focus:outline-none focus:border-violet-400 focus:ring-1 focus:ring-violet-400 disabled:bg-slate-50 disabled:text-slate-500 disabled:border-slate-200 disabled:shadow-none invalid:border-pink-500 invalid:text-pink-600 focus:invalid:border-pink-500 focus:invalid:ring-pink-500" />
        </div>
        <div class="my-3">
          <label for="password" class="block text-sm">Password</label>
          <input type="password" placeholder="ex. password"
            class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400 focus:outline-none focus:border-violet-400 focus:ring-1 focus:ring-violet-40000 disabled:bg-slate-50 disabled:text-slate-500 disabled:border-slate-200 disabled:shadow-none invalid:border-pink-500 invalid:text-pink-600 focus:invalid:border-pink-500 focus:invalid:ring-pink-500" />
        </div>
        <div class="flex justify-center py-2">
          <button @click="login" class="bg-purple-500 hover:bg-violet-500 py-2 px-5 rounded-lg font-medium text-white text-sm duration-200">Sign In</button>
        </div>
      </div>
    </div>
  </div>
</template>
