<script setup>
import { onMounted, ref } from 'vue'

const theme = ref('light')

onMounted(() => {
  const savedTheme = localStorage.getItem('theme') || 'light'
  theme.value = savedTheme
  document.documentElement.setAttribute('data-theme', savedTheme)
})

const toggleTheme = (newTheme) => {
  theme.value = newTheme
  document.documentElement.setAttribute('data-theme', newTheme)
  localStorage.setItem('theme', newTheme)
}
</script>

<template>
  <div id="app" :data-theme="theme">
    <router-view @toggle-theme="toggleTheme" />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

#app {
  min-height: 100vh;
  transition: background-color 0.3s ease, color 0.3s ease;
}
</style>