<template>
  <button
    :class="[
      'flex w-4 h-4 items-center border-solid rounded-md',
      classNameMap[props.colorType],
      { 'drop-shadow-md outline-double outline-stone-300': props.active }
    ]"
  ></button>
</template>
<script setup>
const props = defineProps({
  colorType: {
    type: String,
    default: 'normal',
    validator: (value) => {
      return ['normal', 'warn', 'danger'].includes(value)
    }
  },
  active: {
    type: Boolean,
    default: false
  }
})
const classNameMap = {
  normal: 'normal',
  warn: 'warn',
  danger: 'danger'
}
</script>
<style scoped>
.normal {
  @apply bg-sky-500/50 hover:bg-sky-500/75;
}
.warn {
  @apply bg-yellow-500 hover:bg-yellow-600;
}
.danger {
  @apply bg-red-500 hover:bg-red-600;
}
</style>
