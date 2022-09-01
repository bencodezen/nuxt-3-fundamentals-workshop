<script setup>
import PhotoGallery from './components/PhotoGallery'
import TodoViewer from './components/TodoViewer'
</script>

<template>
  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <TodoViewer title="This is fun!">
            <template v-slot:hero>
              <h3>Whoa this worked!</h3>
            </template>
          </TodoViewer>
        </div>
        <div class="column">
          <PhotoGallery />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import './node_modules/bulma/bulma.sass';
@import './assets/styles/main.scss';

.photo-gallery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
