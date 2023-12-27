<script setup>
import CardPanel, { CARD_TYPE } from '@/components/Card'

const cardList = [
  {
    type: CARD_TYPE.NORMAL,
    title: 'Basic'
  },
  {
    type: CARD_TYPE.WARN,
    title: 'Intermediate'
  },
  {
    type: CARD_TYPE.DANGER,
    title: 'Important'
  }
]
</script>
<template>
  <div class="flex flex-wrap">
    <CardPanel
      v-for="(card, index) in cardList"
      :key="index"
      class="mr-2 mb-2"
      :color-type="card.type"
      :title="card.title"
    />
  </div>
</template>
