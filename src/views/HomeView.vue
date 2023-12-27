<script setup>
import { ref } from 'vue'

import Tab, { TAB_TYPE } from '@/components/Tab'
import Step1Practice from '@/workshop/Step1Practice.vue'
import Step1Solution from '@/workshop/Step1Solution.vue'

const tab = ref(TAB_TYPE.PRACTICE)
const onTabClick = (tabType) => {
  tab.value = tabType
}
</script>

<template>
  <div class="flex h-[calc(100vh-3rem)] flex-col items-center">
    <!-- component -->
    <Tab @tab:click="onTabClick" class="my-10" />

    <Step1Practice v-if="tab === TAB_TYPE.PRACTICE" />
    <Step1Solution v-else />
  </div>
</template>
