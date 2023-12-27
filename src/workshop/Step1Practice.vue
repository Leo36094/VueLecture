<script setup>
import CardPanel, { CARD_TYPE } from '@/components/Card'

/**
 * Expected Result:
 * Three CardPanel with different color and title
 * 1. Blue card witg title "Basic"
 * 2. Yellow card with title "Intermediate"
 * 3. Red card with title "Important"
 *  */
/**
 * Practice Start Here
 * 1. Provide props to CardPanel
 * 2. Use v-for to render multiple CardPanel
 */
</script>

<template>
  <div class="flex flex-wrap">
    <CardPanel class="mr-2 mb-2" />
  </div>
</template>
