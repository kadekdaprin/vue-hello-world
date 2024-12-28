<script setup>
import TodoItem from "./TodoItem.vue"

const { todos } = defineProps(["todos"])
const emit = defineEmits(["toggle"])

const onToggle = (item) => {
  emit("toggle", item)
}

const onDelete = (item) => {
  emit("delete", item)
}
</script>

<template>
  <ul>
    <TodoItem
      v-for="(todo, index) in todos"
      :key="index"
      :item="todo"
      @toggle="onToggle"
      @delete="onDelete"
    />
  </ul>
</template>
