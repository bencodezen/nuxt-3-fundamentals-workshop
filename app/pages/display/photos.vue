<script setup>
import { ref } from 'vue'

let photoGallery = ref([])
</script>

<template>
  <BaseDisplay
    title="Photo Gallery"
    itemType="photos"
    v-model:itemList="photoGallery"
  >
    <template v-slot:hero> </template>
    <template v-slot:items>
      <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
        <img :src="photo.thumbnailUrl" />
      </li>
    </template>
  </BaseDisplay>
</template>

<style lang="scss">
.photo-gallery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
