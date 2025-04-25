<script setup>
import NavBar from './components/NavBar.vue'
</script>

<template>
  <div class="app">
    <NavBar />
    <main class="main-content">
      <router-view />
    </main>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  line-height: 1.6;
  color: #2c3e50;
}

.app {
  min-height: 100vh;
  width: 100%;
}

.main-content {
  padding-top: 4rem;
  width: 100%;
}
</style>
