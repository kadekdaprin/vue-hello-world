<script setup>
import { ref, inject } from "vue"
import { todosKey } from "../keys/keys.js"

const newTodo = ref("")
const { onAddTodo } = inject(todosKey)

const submitTodo = () => {
  if (newTodo.value.trim() === "") return

  onAddTodo(newTodo.value)

  newTodo.value = ""
}
</script>

<template>
  <form @submit.prevent="submitTodo" @keyup.enter="submitTodo">
    <input v-model.lazy="newTodo" placeholder="Enter a new todo" />
    <button type="submit">Add</button>
  </form>
</template>
