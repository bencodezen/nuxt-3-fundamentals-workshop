<script setup>
import { ref } from 'vue'

let photoGallery = ref([])

const route = useRoute()

const filteredPhotoGallery = computed(() => {
  if (route.query.even) {
    return photoGallery.value.filter(photo => photo.albumId % 2 === 0)
  } else {
    return photoGallery.value
  }
})
</script>

<template>
  <BaseDisplay
    title="Photo Gallery"
    itemType="photos"
    v-model:itemList="photoGallery"
  >
    <template v-slot:hero>
      <p>{{ filteredPhotoGallery.length }} photos</p>
    </template>
    <template v-slot:items>
      <li v-for="photo in filteredPhotoGallery" :key="`photo-id-${photo.id}`">
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
