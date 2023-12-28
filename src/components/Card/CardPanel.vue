<template>
  <div :class="['text-slate-200	min-w-48 min-h-72', classNameMap[props.colorType]]">
    <header class="flex justify-between items-center px-2 py-2 bg-slate-200">
      <h2
        v-if="!editMode"
        @dblclick="onTitleDblClick"
        class="text-md font-bold text-center text-slate-600"
      >
        {{ props.title }}
      </h2>
      <input
        v-else
        class="px-2 py-2 text-slate-500"
        v-model="title"
        @keydown.enter="closeInput"
        @blur="closeInput"
      />
      <span
        v-if="props.removeIcon"
        class="material-symbols-outlined ml-auto text-black cursor-pointer"
        @click="emits('delete:click')"
      >
        delete
      </span>
      <ColorButton class="ml-3" :color-type="props.colorType" />
    </header>
    <div class="flex mt-2">
      <slot />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ColorButton from '@/components/ColorButton/ColorButton.vue'
import { CARD_TYPE, classNameMap } from './constants.js'

const props = defineProps({
  colorType: {
    type: String,
    default: CARD_TYPE.NORMAL,
    validator: (value) => {
      return Object.values(CARD_TYPE).includes(value)
    }
  },
  title: {
    type: String,
    default: 'Card'
  },
  removeIcon: {
    type: Boolean,
    default: false
  }
})

const emits = defineEmits(['title:dblclick', 'delete:click'])
const title = ref(props.title)
const editMode = ref(false)

const onTitleDblClick = () => {
  editMode.value = true
}
const closeInput = () => {
  editMode.value = false
  emits('title:dblclick', title.value)
}
</script>
<style scoped>
.normal {
  @apply bg-sky-500/50;
}
.warn {
  @apply bg-yellow-500/90;
}
.danger {
  @apply bg-red-500/50;
}
</style>
