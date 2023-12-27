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

const addTodo = () => {
  todoList.value.push({
    id: new Date().getTime(),
    name: todoInput.value
  })
  todoInput.value = ''
}
const deleteItem = (id) => {
  todoList.value = todoList.value.filter((item) => item.id !== id)
}
</script>

<template>
  <div class="flex flex-col">
    <CardPanel>
      <div class="flex self-end flex-col px-4">
        <BasicInput :value="todoInput" v-model="todoInput" @add:click="addTodo" />

        <CardItem
          v-for="item in todoList"
          :key="item.id"
          :item="item.name"
          @delete:click="deleteItem(item.id)"
        />
      </div>
    </CardPanel>
  </div>
</template>
