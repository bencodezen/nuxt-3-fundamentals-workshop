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
  <div class="section">
    <h1>Photo Gallery</h1>
    <NuxtPage v-if="route.params.id" />
    <BaseDisplay
      v-else
      title="Photo Gallery"
      itemType="photos"
      v-model:itemList="photoGallery"
    >
      <template v-slot:hero>
        <p>{{ filteredPhotoGallery.length }} photos</p>
      </template>
      <template v-slot:items>
        <li v-for="photo in filteredPhotoGallery" :key="`photo-id-${photo.id}`">
          <NuxtLink :to="`/display/photos/${photo.id}`">
            <img :src="photo.thumbnailUrl" />
          </NuxtLink>
        </li>
      </template>
    </BaseDisplay>
  </div>
</template>

<style lang="scss">
.photo-gallery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
