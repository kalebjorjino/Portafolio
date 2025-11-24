<script setup>
import Navbar from '../components/layout/Navbar.vue'
import Footer from '../components/layout/Footer.vue'
import Hero from '../components/sections/Hero.vue'
import About from '../components/sections/About.vue'
import Skills from '../components/sections/Skills.vue'
import Projects from '../components/sections/Projects.vue'
import Contact from '../components/sections/Contact.vue'

const emit = defineEmits(['toggle-theme'])

const handleThemeToggle = (theme) => {
  emit('toggle-theme', theme)
}
</script>

<template>
  <div class="home">
    <Navbar @toggle-theme="handleThemeToggle" />
    
    <main>
      <Hero />
      <About />
      <Skills />
      <Projects />
      <Contact />
    </main>
    
    <Footer />
  </div>
</template>

<style scoped>
.home {
  min-height: 100vh;
}

main {
  padding-top: 73px;
}
</style>