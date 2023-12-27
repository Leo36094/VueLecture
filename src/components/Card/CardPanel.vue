<template>
  <div :class="['text-slate-200	min-w-48 min-h-72 flex-auto', classNameMap[props.colorType]]">
    <header class="flex justify-between items-center px-2 py-2 bg-slate-200">
      <h2 class="text-md font-bold text-center text-slate-600">{{ props.title }}</h2>
      <ColorButton class="ml-3" :color-type="props.colorType" />
    </header>
    <div class="flex mt-2">
      <slot />
    </div>
  </div>
</template>

<script setup>
import ColorButton from '@/components/ColorButton/ColorButton.vue'
import { CARD_TYPE, classNameMap } from './constants.js'

const props = defineProps({
  colorType: {
    type: String,
    default: CARD_TYPE.NORMAL,
    validator: (value) => {
      return Object.values(CARD_TYPE).includes(value)
    }
  },
  title: {
    type: String,
    default: 'Card'
  }
})
</script>
<style scoped>
.normal {
  @apply bg-sky-500/50;
}
.warn {
  @apply bg-yellow-500;
}
.danger {
  @apply bg-red-500;
}
</style>
