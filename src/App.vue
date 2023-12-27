<script setup>
import { RouterView } from 'vue-router'
</script>

<template>
  <nav class="w-full bg-blue-100 text-black">
    <div class="box-border flex px-4 h-12 items-center justify-between">
      <router-link class="px-4 py-2 hover:bg-blue-200" to="/">Vue Basic</router-link>
      <router-link class="px-4 py-2 hover:bg-blue-200" to="/step2">Step 2</router-link>
      <router-link class="px-4 py-2 hover:bg-blue-200" to="/step3">Step 3</router-link>
      <router-link class="px-4 py-2 hover:bg-blue-200" to="/step4">Step 4</router-link>
      <router-link class="px-4 py-2 hover:bg-blue-200" to="/step5">Step 5</router-link>
    </div>
  </nav>
  <div class="container box-border mx-auto flex flex-col items-center">
    <RouterView />
  </div>
</template>
