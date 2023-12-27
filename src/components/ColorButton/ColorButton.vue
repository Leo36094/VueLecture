<template>
  <button
    :class="[
      'flex w-4 h-4 mx-2 my-2 items-center border-solid rounded-md',
      classNameMap[props.colorType]
    ]"
  ></button>
</template>
<script setup>
const props = defineProps({
  colorType: {
    type: String,
    default: 'normal'
  }
})
const classNameMap = {
  normal: 'normal',
  warn: 'warn',
  danger: 'danger'
}

</script>
<style>
.normal {
  @apply bg-cyan-500 hover:bg-cyan-600
}
.warn {
  @apply bg-yellow-500 hover:bg-yellow-600
}
.danger {
  @apply bg-red-500 hover:bg-red-600
}
</style>
