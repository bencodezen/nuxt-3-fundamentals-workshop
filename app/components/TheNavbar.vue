<script setup></script>

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
            <a class="navbar-item"> About </a>
            <a class="navbar-item"> Jobs </a>
            <a class="navbar-item"> Contact </a>
            <hr class="navbar-divider" />
            <a class="navbar-item"> Report an issue </a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<style></style>
