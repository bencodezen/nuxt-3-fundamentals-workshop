<script setup></script>

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
.photo-gallery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
