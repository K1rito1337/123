<template>
  <div class="flex flex-col items-center justify-center min-h-[60vh] bg-gradient-to-br from-gray-100 to-gray-300 rounded-xl shadow-xl p-8 max-w-2xl mx-auto w-full">
    <img src="assets/images/arizonalogo.png" alt="Logo"
      class="w-24 h-24 sm:w-32 sm:h-32 rounded-full border-4 border-white shadow-lg mb-6 transition-transform duration-300 hover:scale-105" />
    <h1 class="text-3xl sm:text-5xl font-bold text-gray-900 mb-4 drop-shadow-lg text-center">Oi sheshen</h1>
    <p class="text-base sm:text-lg text-gray-700 mb-6 text-center max-w-xl">
    
      
    </p>
    <div class="flex flex-col sm:flex-row gap-4 w-full justify-center">
      <NuxtLink to="/lab3" class="px-6 py-2 bg-gray-900 text-white rounded-lg shadow hover:bg-gray-700 transition text-center">Lab3</NuxtLink>
      <NuxtLink to="/lab4" class="px-6 py-2 bg-gray-900 text-white rounded-lg shadow hover:bg-gray-700 transition text-center">Lab4</NuxtLink>
      <NuxtLink to="/lab5" class="px-6 py-2 bg-gray-900 text-white rounded-lg shadow hover:bg-gray-700 transition text-center">Lab5</NuxtLink>
      <NuxtLink to="/lab6" class="px-6 py-2 bg-gray-900 text-white rounded-lg shadow hover:bg-gray-700 transition text-center">Lab6</NuxtLink>
    </div>
  </div>
</template>