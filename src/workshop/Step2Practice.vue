<script setup>
// Uncomment this block, if you want to use ref
// import { ref } from 'vue'

import CardPanel from '@/components/Card'
import CardItem from '@/components/Card/CardItem.vue'
import BasicInput from '@/components/Input/BasicInput.vue'

/**
 * Expected Result:
 * Form Input Bindings: https://vuejs.org/guide/essentials/forms.html
 * 1. BasicInput
 *    - CardItem will be added when click add button
 *    - CardItem will be added when press enter
 * 2. CardItem
 *    - CardItem will be deleted when click delete button
 *  */



/**  Practice Start, Uncomment this block
 const defaultItem = {
   id: new Date().getTime(),
   name: 'Example Todo Item'
 }
 const todoInput = ref('')
 const todoList = ref([defaultItem])

const addTodo = () => {
  // Step1: add todo item
  // Step2: clear input
}
const deleteItem = (id) => {
  // Step3: delete todo item
}
*/
</script>

<template>
  <div class="flex flex-col">
    <CardPanel>
      <div class="flex self-end flex-col px-4">
        <!-- Tips: binding value to todoInput -->
        <!-- Tips: See what event is emit by BasicInput, and use it to update value -->
        <BasicInput />
        <!-- Tips: Use todoList to render list -->
        <CardItem />
      </div>
    </CardPanel>
  </div>
</template>
