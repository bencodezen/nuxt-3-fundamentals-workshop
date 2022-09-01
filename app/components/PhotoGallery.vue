<script setup>
import { computed, ref } from 'vue'

let photoGallery = ref([])

const numberOfPhotos = computed(() => {
  return photoGallery.value.length
})

const evenAlbums = computed(() => {
  return photoGallery.value.filter(item => item.albumId % 2 === 0)
})

const oddAlbums = computed(() => {
  return photoGallery.value.filter(item => !(item.albumId % 2 === 0))
})

function fetchPhotoGallery() {
  fetch('https://jsonplaceholder.typicode.com/photos')
    .then(response => response.json())
    .then(json => {
      photoGallery.value = json
    })
}

const textModel = ref('')
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
  <!-- <h1>Photo Gallery</h1>
  <button @click="fetchPhotoGallery">Fetch Data</button>
  <p>
    {{ numberOfPhotos }} photos ({{ oddAlbums.length }} odd albums |
    {{ evenAlbums.length }} even albums)
  </p>
  <ul class="photo-gallery-list">

  </ul> -->
</template>

<style lang="scss">
.photo-gallery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
