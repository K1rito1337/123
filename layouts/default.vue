<template>
  <div class="flex flex-col min-h-screen">
    <header class="flex flex-row w-full bg-gradient-to-r from-gray-900 via-gray-950 to-gray-900 text-white shadow-md py-4 px-6 relative">
      <div class="basis-1/4 flex items-center justify-start px-4">
        <img src="assets/images/arizonalogo.png" class="w-24 h-24 rounded-full border-4 border-white shadow-lg" alt="Logo" />
      </div>
      <div class="basis-1/4"></div>
      <nav
  :class="{
    'basis-1/2 flex flex-row items-center justify-end px-2 gap-2': !burger || burger,
    'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-gray-900 max-sm:px-0': burger,
    'max-sm:hidden': !burger,}"
>
  <NuxtLink to="/" @click="burger = false" class="px-1 py-2 rounded hover:bg-gray-500 transition max-sm:w-48 max-sm:text-center">Home</NuxtLink>

  <div @click="switch_submenu" class="my-auto p-2 rounded hover:bg-gray-500 hover text-white max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0">Labs
  <div class="flex flex-col absolute  top-full bg-gray-500 text-white w-56 text-center max-sm:relative max-sm:w-full max-sm:bg-gray-700" v-show="submenu">
    <NuxtLink to="/lab3" class="px-4 py-2 hover:bg-gray-500 transition max-sm:text-center">Lab3</NuxtLink>
    <NuxtLink to="/lab4" class="px-4 py-2 hover:bg-gray-500 transition max-sm:text-center">Lab4</NuxtLink>
    <NuxtLink to="/lab5" class="px-4 py-2 hover:bg-gray-500 transition max-sm:text-center">Lab5</NuxtLink>
    <NuxtLink to="/lab6" class="px-4 py-2 hover:bg-gray-500 transition max-sm:text-center">Lab6</NuxtLink>
  </div>
  </div>

  <NuxtLink to="/login" class="px-4 py-2 rounded hover:bg-gray-500 transition max-sm:w-full max-sm:text-center">
    LogIn
  </NuxtLink>
  <NuxtLink to="/logout" class="px-4 py-2 rounded hover:bg-gray-500 transition max-sm:w-full max-sm:text-center">
    LogOut
  </NuxtLink>
</nav>

      <div
  v-if="!burger"
  @click="switch_burger"
  class="sm:hidden flex flex-col justify-between items-center w-8 h-6 cursor-pointer ml-auto"
>
  <span class="h-[3px] w-full bg-white"></span>
  <span class="h-[3px] w-full bg-white"></span>
  <span class="h-[3px] w-full bg-white"></span>
</div>


<div
  v-else
  @click="switch_burger"
  class="sm:hidden flex flex-col justify-between items-center w-8 h-6 cursor-pointer ml-auto"
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
