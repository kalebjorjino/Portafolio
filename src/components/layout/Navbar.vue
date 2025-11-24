<script setup>
import { ref } from 'vue'
import ThemeToggle from '../ui/ThemeToggle.vue'
import Button from '../ui/Button.vue'

const emit = defineEmits(['toggle-theme'])

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const handleThemeToggle = (theme) => {
  emit('toggle-theme', theme)
}

const downloadCV = () => {
  const link = document.createElement('a')
  link.href = '/CV.pdf'
  link.download = 'CV.pdf'
  link.click()
}

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
    isMenuOpen.value = false
  }
}
</script>

<template>
  <nav class="navbar">
    <div class="container navbar-content">
      <div class="navbar-brand" @click="scrollToSection('hero')">
      </div>

      <button class="menu-toggle" @click="toggleMenu" aria-label="Toggle menu">
        <span v-if="!isMenuOpen">☰</span>
        <span v-else>✕</span>
      </button>

      <div class="navbar-menu" :class="{ 'active': isMenuOpen }">
        <a @click="scrollToSection('about')" class="nav-link">Acerca de</a>
        <a @click="scrollToSection('skills')" class="nav-link">Habilidades</a>
        <a @click="scrollToSection('projects')" class="nav-link">Proyectos</a>
        <a @click="scrollToSection('contact')" class="nav-link">Contacto</a>
        
        <Button @click="downloadCV" variant="outline" size="sm">
          📥 Descargar CV
        </Button>
        
        <ThemeToggle @toggle="handleThemeToggle" />
      </div>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: var(--bg);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid var(--border);
  z-index: 1000;
  transition: all 0.3s ease;
}

.navbar-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 20px;
}

.navbar-brand {
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 12px;
}

.profile-pic {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid var(--primary);
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary);
  font-family: 'Courier New', monospace;
}

.menu-toggle {
  display: none;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: var(--text);
}

.navbar-menu {
  display: flex;
  align-items: center;
  gap: 32px;
}

.nav-link {
  color: var(--text);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
  cursor: pointer;
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--primary);
  transition: width 0.3s ease;
}

.nav-link:hover {
  color: var(--primary);
}

.nav-link:hover::after {
  width: 100%;
}

@media (max-width: 768px) {
  .menu-toggle {
    display: block;
  }

  .navbar-menu {
    position: fixed;
    top: 73px;
    left: 0;
    right: 0;
    background: var(--bg);
    flex-direction: column;
    padding: 24px;
    gap: 24px;
    transform: translateX(100%);
    transition: transform 0.3s ease;
    border-bottom: 1px solid var(--border);
  }

  .navbar-menu.active {
    transform: translateX(0);
  }

  .nav-link::after {
    display: none;
  }
}
</style>
