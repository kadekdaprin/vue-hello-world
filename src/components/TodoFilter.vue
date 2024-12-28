<script setup>
const currentFilter = defineProps(["filter"])
</script>

<template>
  <div>
    <button :class="{ active: currentFilter === 'all' }" @click="$emit('filter-change', 'ALL')">
      All
    </button>
    <button
      :class="{ active: currentFilter === 'active' }"
      @click="$emit('filter-change', 'ACTIVE')"
    >
      Active
    </button>
    <button
      :class="{ active: currentFilter === 'completed' }"
      @click="$emit('filter-change', 'COMPLETED')"
    >
      Completed
    </button>
  </div>
</template>

<style>
button.active {
  font-weight: bold;
}
</style>
