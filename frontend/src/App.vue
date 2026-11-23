<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <header class="app-header">
    <p class="app-header__title">PartePro</p>
  </header>

  <main class="app-main">
    <RouterView />
  </main>
</template>

<style scoped>
.app-header {
  padding: 1rem;
  border-bottom: 1px solid var(--color-border);
}

.app-header__title {
  margin: 0;
  font-size: 1.25rem;
  font-weight: 600;
}

.app-main {
  padding: 1rem;
}
</style>
