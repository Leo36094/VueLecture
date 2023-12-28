<script setup>
import { useRoute, RouterView } from 'vue-router'

const route = useRoute()
</script>

<template>
  <nav class="w-full bg-cyan-900 text-stone-300">
    <div class="box-border flex px-4 py-2 h-12 items-center justify-between">
      <router-link class="link" :class="{ 'link-active': route.name === 'home' }" to="/"
        >Vue Basic</router-link
      >
      <router-link class="link" :class="{ 'link-active': route.name === 'step2' }" to="/step2"
        >Events & Form Input Bindings</router-link
      >
      <router-link class="link" :class="{ 'link-active': route.name === 'step3' }" to="/step3"
        >Step 3</router-link
      >
      <router-link class="link" :class="{ 'link-active': route.name === 'final' }" to="/final"
        >Final</router-link
      >
    </div>
  </nav>

  <div class="container box-border mx-auto flex flex-col items-center">
    <RouterView />
  </div>
</template>
<style scoped>
.link {
  @apply px-4 py-1 hover:bg-blue-200 hover:text-black;
}
.link-active {
  @apply text-teal-600 hover:text-black font-bold border-b-2 border-teal-600;
}
</style>
