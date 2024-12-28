<script setup>
const { item } = defineProps(["item"])
</script>

<template>
  <li>
    <input type="checkbox" v-model="item.completed" @click="$emit('toggle', item)" />
    <span :class="{ completed: item.completed }">{{ item.text }}</span>
    <button @click="$emit('delete', item)">X</button>
  </li>
</template>

<style>
.completed {
  text-decoration: line-through;
}
</style>
