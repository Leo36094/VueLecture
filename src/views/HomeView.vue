<script setup>
import ColorButton from '@/components/ColorButton/ColorButton.vue'
import CardPanel from '@/components/Card/CardPanel.vue'
</script>

<template>
  <div>
    <ColorButton />
    <CardPanel color-type="normal" />
    <CardPanel color-type="warn" />
    <CardPanel color-type="danger" />
  </div>
</template>
