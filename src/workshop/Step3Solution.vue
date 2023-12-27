<script setup>
import { ref } from 'vue'

import CardPanel from '@/components/Card'
import CardItem from '@/components/Card/CardItem.vue'
import BasicInput from '@/components/Input/BasicInput.vue'
import ColorButton from '@/components/ColorButton'

const defaultCard = {
  colorType: 'normal',
  title: 'Default',
  id: new Date().getTime(),
  todoInput: ''
}

const defaultItem = {
  id: new Date().getTime(),
  name: 'Example Todo Item'
}

const colorButtons = ['normal', 'warn', 'danger']
const selectedColorIdx = ref(0)
const cardTitle = ref('')
const cardList = ref([defaultCard])
const todoListMap = ref(new Map())
const createCard = () => {
  const id = new Date().getTime()
  const card = () => ({
    colorType: colorButtons[selectedColorIdx.value],
    title: cardTitle.value,
    id,
    todoInput: ''
  })
  cardList.value.push(card())
  todoListMap.value.set(id, [defaultItem])
  cardTitle.value = ''
}
const addTodo = (cardId) => {
  const card = cardList.value.find((card) => card.id === cardId)
  const todoList = todoListMap.value.get(cardId)
  todoList.push({
    id: new Date().getTime(),
    name: card.todoInput
  })
  card.todoInput = ''
}
const updateCardTitle = (cardId, title) => {
  const card = cardList.value.find((card) => card.id === cardId)
  card.title = title
}
</script>

<template>
  <div class="flex flex-col items-center">
    <div class="flex mb-4 items-center">
      <ColorButton
        v-for="(color, idx) in colorButtons"
        class="mx-1"
        :active="selectedColorIdx === idx"
        :key="color"
        :color-type="color"
        @click="selectedColorIdx = idx"
      />
      <BasicInput v-model="cardTitle" @add:click="createCard" label="Card Name" />
    </div>
    <div class="flex flex-wrap content-start">
      <CardPanel
        class="mx-2 my-2"
        v-for="card in cardList"
        :key="card.id"
        :color-type="card.colorType"
        :title="card.title"
        @title:dblclick="(title) => updateCardTitle(card.id, title)"
        remove-icon
      >
        <div class="flex self-end flex-col px-4">
          <BasicInput v-model="card.todoInput" @add:click="addTodo(card.id)" />

          <CardItem
            v-for="item in todoListMap.get(card.id)"
            :color-type="card.colorType"
            :key="item.id"
            :item="item.name"
            @delete:click="deleteItem(item.id)"
          />
        </div>
      </CardPanel>
    </div>
  </div>
</template>
