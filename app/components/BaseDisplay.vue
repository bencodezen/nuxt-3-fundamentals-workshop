<script setup>
import { defineEmits, defineProps, ref } from 'vue'

const props = defineProps({
  itemList: {
    type: Array,
    default: () => []
  },
  itemType: {
    type: String,
    required: true
  },
  title: {
    type: String,
    required: true
  }
})

const emit = defineEmits(['update:itemList'])

function fetchItemList() {
  fetch(`https://jsonplaceholder.typicode.com/${props.itemType}`)
    .then(response => response.json())
    .then(json => {
      emit('update:itemList', json)
    })
}
</script>

<template>
  <!-- Generic Template -->
  <div class="section">
    <slot name="hero" />
    <h1 class="title">{{ title }}</h1>
    <button @click="fetchItemList">Fetch Data</button>
    <slot name="metrics" />
    <ul class="list">
      <slot name="items" :itemList="itemList" />
    </ul>
  </div>
</template>

<style></style>
