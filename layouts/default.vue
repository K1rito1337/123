<template>
  <div class="flex flex-col min-h-screen">
    <header class="w-full bg-gradient-to-r from-gray-900 via-gray-950 to-gray-900 text-white shadow-md py-4 px-6 relative z-50">
  <div class="flex items-center justify-between">
    <!-- Logo -->
    <div class="flex items-center space-x-4">
      <img src="assets/images/arizonalogo.png" class="w-14 h-14 rounded-full border-4 border-white shadow-lg" alt="Logo" />
    </div>

    <!-- Desktop Nav -->
    <nav class="hidden sm:flex items-center gap-6 text-sm font-medium">
      <NuxtLink to="/" class="hover:text-gray-300 transition">Home</NuxtLink>

      <div class="relative group">
        <button class="hover:text-gray-300 transition">Labs</button>
        <div class="absolute hidden group-hover:flex flex-col mt-2 bg-gray-800 rounded shadow-lg z-40 min-w-[120px]">
          <NuxtLink to="/lab3" class="px-4 py-2 hover:bg-gray-700">Lab3</NuxtLink>
          <NuxtLink to="/lab4" class="px-4 py-2 hover:bg-gray-700">Lab4</NuxtLink>
          <NuxtLink to="/lab5" class="px-4 py-2 hover:bg-gray-700">Lab5</NuxtLink>
          <NuxtLink to="/lab6" class="px-4 py-2 hover:bg-gray-700">Lab6</NuxtLink>
        </div>
      </div>

      <NuxtLink to="/login" class="hover:text-gray-300 transition">LogIn</NuxtLink>
      <NuxtLink to="/logout" class="hover:text-gray-300 transition">LogOut</NuxtLink>
    </nav>

    <!-- Burger -->
    <button @click="switch_burger" class="sm:hidden flex flex-col justify-center items-center space-y-1">
      <span :class="['w-6 h-[2px] bg-white transition', burger ? 'rotate-45 translate-y-[7px]' : '']"></span>
      <span :class="['w-6 h-[2px] bg-white transition', burger ? 'opacity-0' : '']"></span>
      <span :class="['w-6 h-[2px] bg-white transition', burger ? '-rotate-45 -translate-y-[7px]' : '']"></span>
    </button>
  </div>

  <!-- Mobile Menu -->
   <transition name="fade">
    <div v-if="burger" class="flex flex-col gap-3 mt-4 sm:hidden bg-gray-900 p-4 rounded-md z-40">
      <NuxtLink to="/" @click="switch_burger" class="text-white text-center">Home</NuxtLink>

      <button @click="switch_submenu" class="text-white text-center">Labs</button>
      <div v-if="submenu" class="flex flex-col gap-1 bg-gray-800 rounded p-2 text-sm">
        <NuxtLink to="/lab3" class="hover:bg-gray-700 px-2 py-1 rounded">Lab3</NuxtLink>
        <NuxtLink to="/lab4" class="hover:bg-gray-700 px-2 py-1 rounded">Lab4</NuxtLink>
        <NuxtLink to="/lab5" class="hover:bg-gray-700 px-2 py-1 rounded">Lab5</NuxtLink>
        <NuxtLink to="/lab6" class="hover:bg-gray-700 px-2 py-1 rounded">Lab6</NuxtLink>
      </div>

      <NuxtLink to="/login" @click="switch_burger" class="text-white text-center">LogIn</NuxtLink>
      <NuxtLink to="/logout" @click="switch_burger" class="text-white text-center">LogOut</NuxtLink>
    </div>
  </transition>


      
      <div
        v-if="!burger"
        @click="switch_burger"
        class="z-50 cursor-pointer hidden max-sm:flex flex-col mr-4 justify-between items-center w-8 h-6"
      >
        <span class="h-[3px] w-full bg-white"></span>
        <span class="h-[3px] w-full bg-white"></span>
        <span class="h-[3px] w-full bg-white"></span>
      </div>
      <div
        v-else
        @click="switch_burger"
        class="z-50 cursor-pointer hidden max-sm:flex flex-col mr-4 justify-between items-center w-8 h-6"
      >
        <span class="h-[3px] w-full bg-white rotate-45 relative top-[9px]"></span>
        <span class="h-[3px] w-full bg-white opacity-0"></span>
        <span class="h-[3px] w-full bg-white -rotate-45 relative bottom-[9px]"></span>
      </div>
    </header>

    
    <main class="flex-grow flex flex-col items-center justify-center bg-gray-100 py-12 px-4">
      <slot />
    </main>

   
    <footer class="w-full bg-gray-800 text-white py-6">
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
