<script setup>
import { ref, onMounted } from 'vue'

const emit = defineEmits(['toggle'])

const isDark = ref(false)

onMounted(() => {
  isDark.value = localStorage.getItem('theme') === 'dark'
})

const toggle = () => {
  isDark.value = !isDark.value
  emit('toggle', isDark.value ? 'dark' : 'light')
}
</script>

<template>
  <button 
    class="theme-toggle" 
    @click="toggle"
    :aria-label="`Switch to ${isDark ? 'light' : 'dark'} mode`"
  >
    <span class="icon sun" v-if="!isDark">☀️</span>
    <span class="icon moon" v-else>🌙</span>
  </button>
</template>

<style scoped>
.theme-toggle {
  background: var(--card);
  border: 2px solid var(--border);
  border-radius: 50%;
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
}

.theme-toggle:hover {
  transform: scale(1.1) rotate(15deg);
  border-color: var(--primary);
}

.icon {
  font-size: 1.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (max-width: 768px) {
  .theme-toggle {
    width: 44px;
    height: 44px;
  }
  
  .icon {
    font-size: 1.25rem;
  }
}
</style>