<script setup>
import { defineProps, ref, computed } from 'vue'

defineProps({
  title: {
    type: String,
    default: 'Hello Frontend Masters!'
  }
})

const todoList = ref([])

const completedItems = computed(() => {
  return todoList.value.filter(item => item.completed)
})

const remainingItems = computed(() => {
  return todoList.value.filter(item => !item.completed)
})

function fetchTodoList() {
  fetch('https://jsonplaceholder.typicode.com/todos/')
    .then(response => response.json())
    .then(json => {
      todoList.value = json
    })
}
</script>

<template>
  <div class="section">
    <slot name="hero" />
    <h1 class="title">{{ title }}</h1>
    <button @click="fetchTodoList">Fetch Data</button>
    <slot
      name="metrics"
      :completed="completedItems"
      :remaining="remainingItems"
    >
      <p>
        {{ completedItems.length }} completed |
        {{ remainingItems.length }} remaining
      </p>
    </slot>
    <ul class="list">
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
      </li>
    </ul>
  </div>
</template>

<style lang="scss"></style>
