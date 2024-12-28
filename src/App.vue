<script setup>
import { ref, computed, provide } from "vue"

import TodoList from "./components/TodoList.vue"
import TodoInput from "./components/TodoInput.vue"
import TodoFilter from "./components/TodoFilter.vue"
import { todosKey } from "./keys/keys.js"

const todos = ref([
  {
    text: "beli tissue",
    completed: false,
  },
  {
    text: "beli popok",
    completed: true,
  },
])

const onAddTodo = (newTodo) => {
  todos.value.push({
    text: newTodo,
    completed: false,
  })
}

provide(todosKey, {
  todos,
  onAddTodo,
})

const filter = ref("ALL")

const onDelete = (item) => {
  todos.value = todos.value.filter((todo) => todo !== item)
}

const onToggle = (item) => {
  todo.value[item].completed = !todo.value[item].completed
}

const onFilterChange = (newFilter) => {
  filter.value = newFilter
}

const filterTodos = computed(() => {
  switch (filter.value) {
    case "ALL":
      return todos.value
    case "ACTIVE":
      return todos.value.filter((todo) => !todo.completed)
    case "COMPLETED":
      return todos.value.filter((todo) => todo.completed)
  }
})
</script>

<template>
  <h1>Todo List</h1>
  <TodoInput />
  <TodoFilter @filter-change="onFilterChange" />
  <TodoList :todos="filterTodos" @delete="onDelete" @toggle="onToggle" />
</template>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin: 20px;
}
</style>
