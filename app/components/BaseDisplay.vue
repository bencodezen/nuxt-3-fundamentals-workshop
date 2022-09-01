<script setup>
import { defineEmits, defineProps, ref } from 'vue'

const props = defineProps({
  itemList: {
    type: Array,
    default: () => []
  },
  title: {
    type: String,
    required: true
  }
})

const route = useRoute()

const itemType = route.path.split('/')[2]

const emit = defineEmits(['update:itemList'])

fetch(`https://jsonplaceholder.typicode.com/${itemType}`)
  .then(response => response.json())
  .then(json => {
    emit('update:itemList', json)
  })
</script>

<template>
  <!-- Generic Template -->
  <div class="section">
    <slot name="hero" />
    <h1 class="title">{{ title }}</h1>
    <slot name="metrics" />
    <ul class="list">
      <slot name="items" :itemList="itemList" />
    </ul>
  </div>
</template>

<style></style>
