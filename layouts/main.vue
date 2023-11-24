<template>
  <div class="bg-violet-100">
    <slot />
  </div>
  <footer class="w-full bg-neutral-800 text-white pt-12 pb-3">
    <div class="px-5 max-w-[1200px] mx-auto">
      <div class="flex text-white flex-wrap">
        <div class="w-full md:w-1/2 order-2 md:order-1">
          <div class="text-3xl md:text-4xl font-medium italic text-center md:text-left">Travel45</div>
          <div class="flex mt-2 md:mt-5 justify-center md:justify-start">
            <a href="https://twitter.com" target="blank" class="hover:text-cyan-400 mx-3" title="Twitter">
              <Icon name="twitter" :size="24" />
            </a>
            <a href="https://instagram.com" target="blank" class="hover:text-pink-500 mx-3" title="Instagram">
              <Icon name="instagram" :size="24" />
            </a>
            <a href="https://facebook.com" target="blank" class="hover:text-blue-400 mx-3" title="Facebook">
              <Icon name="facebook" :size="24" />
            </a>
            <a href="https://whatsapp.com" target="blank" class="hover:text-green-400 mx-3" title="Whatsapp">
              <Icon name="whatsapp" :size="24" />
            </a>
          </div>
        </div>
        <div class="w-full md:w-1/2 mb-10 md:mb-0 order-1 md:order-2">
          <div class="text-center md:text-right">Subscribe to our Newsletter for future information.</div>
          <div class="flex flex-wrap justify-center md:justify-end items-center">
            <div class="px-2 mt-3 md:mt-5 mb-5">
              <input type="email" class="rounded py-2 px-4 bg-transparent border" placeholder="example@email.com">
            </div>
            <button class="rounded uppercase px-3 py-2 bg-cyan-500 hover:bg-cyan-600 text-sm">Subscribe</button>
          </div>
        </div>
      </div>
      <div class="text-center md:text-base text-sm pt-4 pb-2 mt-10 border-t border-neutral-300">Copyright&copy; 2023. All
        Right Reserved</div>
    </div>
  </footer>
</template>
