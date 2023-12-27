<template>
  <div class="card w-24 flex-auto">
    <ColorButton :color-type="props.colorType" />
  </div>
</template>

<script setup>
import ColorButton from '@/components/ColorButton/ColorButton.vue'
const props = defineProps({
  colorType: {
    type: String
  }
})
</script>
