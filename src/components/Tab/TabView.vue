<template>
  <div class="flex space-x-4 bg-white p-1 rounded">
    <div v-for="(icon, idx) in tabs" :key="idx">
      <button
        @click="setActiveIndex(idx)"
        :class="{ 'bg-gray-200': activeIndex === idx }"
        class="text-gray-800 hover:bg-gray-200 font-bold p-2 rounded transition-colors duration-300"
      >
        <span class="material-symbols-outlined">{{ icon }}</span>
      </button>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import { TAB_TYPE } from './constants.js'
const activeIndex = ref(0)

const tabs = [TAB_TYPE.PRACTICE, TAB_TYPE.SOLUTION]

const setActiveIndex = (index) => {
  activeIndex.value = index
  emits('tab:click', tabs[index])
}

const emits = defineEmits(['click:tab'])
</script>
