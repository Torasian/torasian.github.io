<script setup>
import { ref } from 'vue'

defineProps({
  msg: {
    type: String,
    required: true,
  },
})

const isHovered = ref(false)
</script>

<template>
  <div class="p-8 max-w-2xl mx-auto">
    <div class="bg-white rounded-lg shadow-lg p-6 transition-all duration-300 hover:shadow-xl"
      :class="{ 'transform scale-105': isHovered }" @mouseenter="isHovered = true" @mouseleave="isHovered = false">
      <h1 class="text-4xl font-bold text-emerald-600 mb-4">{{ msg }}</h1>
      <h3 class="text-lg text-gray-700 mb-6">
        You've successfully created a project with
        <a href="https://vite.dev/" target="_blank" rel="noopener"
          class="text-blue-600 hover:text-blue-800 transition-colors duration-200">Vite</a> +
        <a href="https://vuejs.org/" target="_blank" rel="noopener"
          class="text-green-600 hover:text-green-800 transition-colors duration-200">Vue 3</a>.
      </h3>
      <div class="flex gap-4">
        <button class="px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600 transition-colors duration-200">
          Click me!
        </button>
        <button
          class="px-4 py-2 border-2 border-gray-300 rounded-md hover:border-gray-400 transition-colors duration-200">
          Secondary
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
