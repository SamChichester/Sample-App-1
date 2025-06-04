<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav>
      <div class="px-4 py-3 flex items-center">
        <div class="flex items-center space-x-6">
          <RouterLink to="/" class="block text-gray-700 hover:text-blue-600 px-3 py-2">Home</RouterLink>
        </div>
        <div class="flex items-center space-x-6">
          <RouterLink to="/about" class="block text-gray-700 hover:text-blue-600 px-3 py-2">About</RouterLink>
        </div>
        <div class="flex items-center space-x-6">
          <RouterLink to="/api-test" class="block text-gray-700 hover:text-blue-600 px-3 py-2">API Test</RouterLink>
        </div>
      </div>
    </nav>
  </header>

  <RouterView />
</template>