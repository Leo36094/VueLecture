<script setup>
import { ref } from 'vue'

import CardPanel from '@/components/Card'
import CardItem from '@/components/Card/CardItem.vue'
import BasicInput from '@/components/Input/BasicInput.vue'
import ColorButton from '@/components/ColorButton'

// Data structure for todoList
const defaultCard = {
  colorType: 'normal',
  title: 'Default',
  id: new Date().getTime(),
  // For Card title input
  todoInput: ''
}

// Data structure for todoList Item
const defaultItem = {
  id: new Date().getTime(),
  name: 'Example Todo Item'
}

/**
 * Expected Result:
 * - ColorButton Component
 *  1. Three types of color buttons will be rendered
 *  2. When user click on the color button, the color will be selected
 * - BasicInput Component (First one)
 *  1. A new Card will be created when user click on the '+' button
 *  2. The color of the new Card will be the selected color
 *  3. The title of the new Card will be the input value
 * - CardPanel Component
 *  1. The Card will have a delete button on the top right corner
 *  2. The Card can be deleted when user click on the delete button
 *  3. The Card can add todo item when user click on the '+' button
 *  4. The Card can edit the title when user double click the title
 * - CardItem Component
 *  1. The CardItem can be deleted when user click on the delete button
 */

const colorButtons = ['normal', 'warn', 'danger']
const selectedColorIdx = ref(0)
const cardTitle = ref('')
const cardList = ref([defaultCard])

const createCard = (title) => {}
const addTodo = (card) => {}
const updateCardTitle = (cardId, title) => {}
</script>

<template>
  <div class="flex flex-col items-center">
    <div class="flex mb-4 items-center">
      <!-- Tips
        1. Use @click to update selectedColorIdx
        2. Use :active to set active color
        3. Use :color-type to set color type
      -->
      <ColorButton v-for="(color, idx) in colorButtons" class="mx-1" :key="idx" />
      <!-- Tips
        1. Use @add:click to create a new card
        2. Use v-model to bind the input value
        3. Use label prop to set the label
       -->
      <BasicInput />
    </div>
    <div class="flex flex-wrap content-start">
      <!-- Tips
        1. Use v-for to render the cardList
        2. Use :key to set the key
        3. Use @title:dbclick to update the card title
        4. Use @delete:click to delete the card
        5. Use :color-type to set the color type
        6. Use title prop to set the title
        7. Use remove-icon prop to display the delete button
      -->
      <CardPanel class="mx-2 my-2" v-for="card in cardList" :key="card.id">
        <div class="flex self-end flex-col px-4">
          <!-- Tips
            1. Use v-model to bind the input value
            2. Use @add:click to add todo item
           -->
          <BasicInput />
          <!-- Tips
            1. Use v-for to render the todoList
            2. Use :key to set the key
            3. Use :color-type to set the color type
            4. Use :item to set the item name
            5. Use @delete:click to delete the item
          -->
          <CardItem />
        </div>
      </CardPanel>
    </div>
  </div>
</template>
