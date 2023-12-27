<script setup>
import { ref } from 'vue'

import CardPanel from '@/components/Card'
import CardItem from '@/components/Card/CardItem.vue'
import BasicInput from '@/components/Input/BasicInput.vue'

const defaultItem = {
  id: new Date().getTime(),
  name: 'Example Todo Item'
}

const todoInput = ref('')
const todoList = ref([defaultItem])

/**  Practice Start, Uncomment this block

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
        <BasicInput :value="todoInput" @input="(val) => (todoInput = val)" />
        <CardItem v-for="item in todoList" :key="item.id" :item="item.name" />
      </div>
    </CardPanel>
  </div>
</template>
