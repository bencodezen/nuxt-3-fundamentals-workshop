<script setup>
const route = useRoute()
</script>

<template>
  <h2>This is task id: {{ route.params }}</h2>
</template>

<style></style>
