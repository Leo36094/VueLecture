<script setup>
import { ref, onMounted } from 'vue'
import draggable from 'vuedraggable'

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

const createCard = (title) => {
  const id = new Date().getTime()
  const card = {
    colorType: colorButtons[selectedColorIdx.value],
    title,
    id,
    todoInput: ''
  }
  cardList.value.push(card)
  todoListMap.value.set(id, [defaultItem])
  cardTitle.value = ''
}
const addTodo = (card) => {
  const { id: cardId, todoInput } = card

  if (todoInput === '') return
  const todoList = todoListMap.value.get(cardId)
  todoList.push({
    id: new Date().getTime(),
    name: todoInput
  })
  card.todoInput = ''
}
const updateCardTitle = (cardId, title) => {
  const card = cardList.value.find((card) => card.id === cardId)
  card.title = title
}

const deleteCard = (cardId) => {
  cardList.value = cardList.value.filter((card) => card.id !== cardId)
  todoListMap.value.delete(cardId)
}

const deleteItem = (cardId, itemId) => {
  const todoList = todoListMap.value.get(cardId)
  todoListMap.value.set(
    cardId,
    todoList.filter((item) => item.id !== itemId)
  )
}

const dragOptions = {
  animation: 200,
  group: 'description',
  disabled: false,
  ghostClass: 'ghost'
}

const drag = ref(false)

onMounted(() => {
  todoListMap.value.set(defaultCard.id, [defaultItem])
})
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
      <BasicInput v-model="cardTitle" @add:click="createCard(cardTitle)" label="Card Name" />
    </div>
    <div>
      <draggable
        class="flex flex-wrap content-start"
        :list="cardList"
        :component-data="{
          tag: 'ul',
          type: 'transition-group',
          name: !drag ? 'flip-list' : null
        }"
        @start="drag = true"
        @end="drag = false"
        v-bind="dragOptions"
        itemKey="id"
      >
        <template #item="{ element: card }">
          <CardPanel
            class="mx-2 my-2"
            :key="card.id"
            :color-type="card.colorType"
            :title="card.title"
            @title:dblclick="(title) => updateCardTitle(card.id, title)"
            @delete:click="deleteCard(card.id)"
            remove-icon
          >
            <div class="flex self-end flex-col px-4">
              <BasicInput v-model="card.todoInput" @add:click="addTodo(card)" />

              <CardItem
                v-for="item in todoListMap.get(card.id)"
                :color-type="card.colorType"
                :key="item.id"
                :item="item.name"
                @delete:click="deleteItem(card.id, item.id)"
              />
            </div>
          </CardPanel>
        </template>
      </draggable>
    </div>
  </div>
</template>
<style>
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
</style>
