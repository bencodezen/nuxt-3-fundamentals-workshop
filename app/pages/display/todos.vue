<script setup>
import { ref, computed } from 'vue'

const todoList = ref([])

const route = useRoute()

const filteredTodoList = computed(() => {
  if (route.query.completed) {
    return completedItems.value
  } else {
    return remainingItems.value
  }
})

const completedItems = computed(() => {
  return todoList.value.filter(item => item.completed)
})

const remainingItems = computed(() => {
  return todoList.value.filter(item => !item.completed)
})
</script>

<template>
  <div class="section">
    <h1 class="title">Todo Viewer</h1>
    <NuxtPage v-if="route.params.id" />
    <BaseDisplay v-else title="Todo Viewer" v-model:itemList="todoList">
      <template v-slot:hero> </template>
      <template v-slot:metrics>
        {{ completedItems.length }} completed |
        {{ remainingItems.length }} remaining
      </template>
      <template v-slot:items>
        <li v-for="todo in filteredTodoList" :key="`todo-id-${todo.id}`">
          <input type="checkbox" :checked="todo.completed" />
          <NuxtLink :to="`/display/todos/${todo.id}`">{{
            todo.title
          }}</NuxtLink>
        </li>
      </template>
    </BaseDisplay>
  </div>
</template>

<style lang="scss"></style>
