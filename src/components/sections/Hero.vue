<script setup>
import Button from '../ui/Button.vue'

const scrollToContact = () => {
  const element = document.getElementById('contact')
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<template>
  <section id="hero" class="hero">
    <div class="hero-content">
      <div class="hero-text">
        <h1 class="hero-title">
          Hola, Me llamo <span class="highlight">Jorjino</span>
        </h1>
        <h2 class="hero-subtitle">Full Stack Developer | Systems & Server Administrator | Spring Boot</h2>
        <p class="hero-description">
          Profesional apasionado por la tecnología especializado en desarrollo backend con Spring Boot, administración de sistemas Linux y optimización de infraestructura. He creado soluciones en entornos reales como sistemas de control de asistencia y registro de visitas para instituciones públicas. Trabajo con buenas prácticas, integración de servicios y gestión de servidores open source usando Proxmox.
        </p>
        <div class="hero-buttons">
          <Button @click="scrollToContact" size="lg">
            Ponte en contacto 💬
          </Button>
          <Button variant="outline" size="lg" @click="$router.push('/#projects')">
            Ver Proyectos 🚀
          </Button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 80vh; /* Reducido para ser menos "pantalla completa" */
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  padding: 120px 20px; /* Más padding para compensar la altura */
  text-align: center;
}

.hero-content {
  position: relative;
  z-index: 1;
  max-width: 800px;
  margin: 0 auto;
}

.hero-text {
  animation: fadeIn 1s ease-out;
}

.hero-title {
  font-size: clamp(2.5rem, 6vw, 4rem);
  font-weight: 800;
  margin-bottom: 1rem;
  line-height: 1.2;
}

.highlight {
  color: var(--primary);
  position: relative;
  display: inline-block;
}

.highlight::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 8px;
  background: var(--primary);
  opacity: 0.3;
  z-index: -1;
}

.hero-subtitle {
  font-size: clamp(1.5rem, 4vw, 2.5rem);
  font-weight: 600;
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
}

.hero-description {
  font-size: clamp(1rem, 2vw, 1.25rem);
  color: var(--text-secondary);
  line-height: 1.8;
  margin-bottom: 2.5rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .hero {
    min-height: 70vh;
    padding: 80px 20px;
  }

  .hero-buttons {
    flex-direction: column;
    width: 100%;
  }

  .hero-buttons button {
    width: 100%;
  }
}
</style>
