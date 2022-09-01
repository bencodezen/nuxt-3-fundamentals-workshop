<script>
import { defineNuxtComponent } from '#app'

export default defineNuxtComponent({
  data: () => ({
    photoGallery: []
  }),
  computed: {
    numberOfPhotos() {
      return this.photoGallery.length
    },
    evenAlbums() {
      return this.photoGallery.filter(item => item.albumId % 2 === 0)
    },
    oddAlbums() {
      return this.photoGallery.filter(item => !(item.albumId % 2 === 0))
    }
  },
  methods: {
    fetchPhotoGallery() {
      fetch('https://jsonplaceholder.typicode.com/photos')
        .then(response => response.json())
        .then(json => {
          this.photoGallery = json
        })
    }
  }
})
</script>

<template>
  <h1>Photo Gallery</h1>
  <button @click="fetchPhotoGallery">Fetch Data</button>
  <p>
    {{ numberOfPhotos }} photos ({{ oddAlbums.length }} odd albums |
    {{ evenAlbums.length }} even albums)
  </p>
  <ul>
    <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
      <img :src="photo.thumbnailUrl" />
    </li>
  </ul>
</template>

<style></style>
