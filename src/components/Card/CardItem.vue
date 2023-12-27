<script setup>
import { classNameMap, CARD_TYPE } from './constants.js'
const props = defineProps({
  colorType: {
    type: String,
    default: CARD_TYPE.NORMAL,
    validator: (value) => {
      return Object.values(CARD_TYPE).includes(value)
    }
  },
  item: {
    type: String,
    default: ''
  }
})
const emits = defineEmits(['delete:click'])
</script>

<template>
  <div
    class="max-w-full flex-wrap rounded-md py-2 flex my-2 px-2 justify-between"
    :class="classNameMap[props.colorType]"
  >
    <p class="w-60">
      {{ props.item }}
    </p>
    <span
      class="material-symbols-outlined self-end cursor-pointer ml-2"
      @click="emits('delete:click')"
    >
      delete
    </span>
  </div>
</template>
<style scoped>
.normal {
  @apply bg-sky-600/75;
}
.warn {
  @apply bg-yellow-600/75;
}

.danger {
  @apply bg-red-600/75;
}
</style>
