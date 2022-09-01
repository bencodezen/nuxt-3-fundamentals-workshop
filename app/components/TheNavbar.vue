<script setup>
const completedCheck = ref(boolean)
const todoQuery = computed => `?completed=${completedCheck}`
</script>

<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io"> MyRecs </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-start"></div>

      <div class="navbar-end">
        <NuxtLink to="/" class="navbar-item"> Home </NuxtLink>

        <div class="navbar-item has-dropdown is-hoverable">
          <NuxtLink to="/display" class="navbar-link"> Display </NuxtLink>

          <div class="navbar-dropdown">
            <NuxtLink to="/display/photos" class="navbar-item">
              Photos
            </NuxtLink>
            <NuxtLink to="/display/todos" class="navbar-item"> Todos </NuxtLink>
            <NuxtLink to="'/display/todos' + todoQuery" class="navbar-item">
              Completed Todos
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<style></style>
