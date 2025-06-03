<template>
  <div class="flex flex-col min-h-screen">
    <header class="flex w-full items-center justify-between bg-gray-900 shadow-sm py-2 sticky top-0 z-50 text-gray-500">
      <div class="basis-1/4 flex items-center justify-start px-8 min-w-40 max-sm:basis-auto">
        <img src="assets/images/arizonalogo.png"
     class="w-16 h-16 bg-white rounded-full p-1 shadow-md hover:scale-110 transition-transform"
     alt="Logo" />
      </div>
      <div class="basis-1/4 max-sm:basis-auto"></div>
      <nav
  :class="{
    'basis-1/2 flex flex-row items-center justify-end px-2 gap-2': !burger || burger,
    'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-gray-900 max-sm:px-0': burger,
    'max-sm:hidden': !burger,}"
>
  <NuxtLink to="/" @click="burger = false" class="my-auto p-2 rounded hover:bg-gray-500 hover text-white max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">Home</NuxtLink>

  <div class="relative">
  <div @click="switch_submenu" class="my-auto p-2 rounded hover:bg-gray-500 text-white cursor-pointer max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">
    Labs
  </div>
  <div
    class="flex flex-col absolute right-0 top-full bg-gray-900 text-white w-56 text-left shadow-lg rounded mt-1 z-40 max-sm:static max-sm:w-56 max-sm:mx-auto max-sm:mt-2"
    v-show="submenu"
  >
    <NuxtLink to="/lab3" class="px-4 py-2 hover:bg-gray-700 transition">Lab3</NuxtLink>
    <NuxtLink to="/lab4" class="px-4 py-2 hover:bg-gray-700 transition">Lab4</NuxtLink>
    <NuxtLink to="/lab5" class="px-4 py-2 hover:bg-gray-700 transition">Lab5</NuxtLink>
    <NuxtLink to="/lab6" class="px-4 py-2 hover:bg-gray-700 transition">Lab6</NuxtLink>
  </div>
</div>

  <NuxtLink to="/login" class="my-auto p-2 rounded hover:bg-gray-500 hover text-white max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">
    LogIn
  </NuxtLink>
  <NuxtLink to="/logout" class="my-auto p-2 rounded hover:bg-gray-500 hover text-white max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">
    LogOut
  </NuxtLink>
</nav>

      <div
  v-if="!burger"
  @click="switch_burger"
  class="max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6"
>
  <span class="h-[3px] w-full bg-white"></span>
  <span class="h-[3px] w-full bg-white"></span>
  <span class="h-[3px] w-full bg-white"></span>
</div>


<div
  v-else
  @click="switch_burger"
  class="max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6"
>
  <span class="h-[3px] w-full bg-white rotate-45 relative top-[9px]"></span>
  <span class="h-[3px] w-full bg-white opacity-0"></span>
  <span class="h-[3px] w-full bg-white rotate-[-45deg] relative bottom-3"></span>
</div>
    </header>
    
    <main class="p-5 flex bg-gray-300 h-screen">
      <slot />
    </main>

   
    <footer class="w-full bg-gray-900 text-white py-6">
      <div class="flex justify-center gap-8">
        <a href="https://www.youtube.com/" target="_blank" rel="noopener">
          <img src="assets/images/youtube.png" class="w-12 h-12 hover:scale-110 transition-transform" alt="YouTube" />
        </a>
        <a href="https://github.com/" target="_blank" rel="noopener">
          <img src="assets/images/github.png" class="w-12 h-12 hover:scale-110 transition-transform" alt="GitHub" />
        </a>
        <a href="https://www.facebook.com/" target="_blank" rel="noopener">
          <img src="assets/images/facebook.png" class="w-12 h-12 hover:scale-110 transition-transform" alt="Facebook" />
        </a>
      </div>
      <p class="mt-4 text-sm text-gray-400">© 2025 Your Company. All rights reserved.</p>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useHead } from '#app'
useHead({
  script: [
    {
      async: true,
      src: 'https://www.googletagmanager.com/gtag/js?id=G-9SKVQGS9YV',
    },
    {
      innerHTML: `
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'G-9SKVQGS9YV');
      `,
      type: 'text/javascript',
    },
  ],
  __dangerouslyDisableSanitizersByTagID: {
    gtag: ['innerHTML'],
  },
})

const burger = ref(false)
const submenu = ref(false)

const switch_burger = () => {
  burger.value = !burger.value
  if (!burger.value) submenu.value = false
}

const switch_submenu = () => {
  submenu.value = !submenu.value
}
</script>