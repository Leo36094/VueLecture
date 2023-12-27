<script setup>
import { ref } from 'vue'

import Tab, { TAB_TYPE } from '@/components/Tab'

const tab = ref(TAB_TYPE.PRACTICE)
const onTabClick = (tabType) => {
  tab.value = tabType
}
</script>

<template>
  <div class="flex h-[calc(100vh-3rem)] flex-col items-center">
    <!-- component -->
    <Tab @tab:click="onTabClick" class="my-10" />
    <keep-alive>
      <template v-if="tab === TAB_TYPE.PRACTICE">
        <slot name="practice" />
      </template>
      <template v-else>
        <slot name="solution" />
      </template>
    </keep-alive>
  </div>
</template>
