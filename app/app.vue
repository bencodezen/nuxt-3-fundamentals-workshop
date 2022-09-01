<script>
import { ref, computed } from 'vue'

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
  <p>
    Photo by
    <a
      href="https://unsplash.com/@glenncarstenspeters?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
      >Glenn Carstens-Peters</a
    >
    on
    <a
      href="https://unsplash.com/s/photos/todo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
      >Unsplash</a
    >
  </p>
  <h1>Hello Frontend Masters!</h1>
  <button @click="fetchTodoList">Fetch Data</button>
  <p>
    {{ completedItems.length }} completed |
    {{ remainingItems.length }} remaining
  </p>
  <ul>
    <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
      <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
    </li>
  </ul>
</template>
