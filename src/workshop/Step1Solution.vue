<script setup>
import CardPanel from '@/components/Card/CardPanel.vue'

const cardList = [
  {
    type: 'normal',
    title: 'Basic'
  },
  {
    type: 'warn',
    title: 'Intermediate'
  },
  {
    type: 'danger',
    title: 'Important'
  }
]
</script>
<template>
  <div class="flex">
    <CardPanel
      v-for="(card, index) in cardList"
      :key="index"
      class="mr-2"
      :color-type="card.type"
      :title="card.title"
    />
  </div>
</template>
