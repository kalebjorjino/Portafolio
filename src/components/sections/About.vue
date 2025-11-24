<script setup>
const stats = [
  { number: '4+', label: 'Años Experiencia' },
  { number: '3+', label: 'Proyectos Principales' },
  { number: '14+', label: 'Tecnologías' },
]
</script>

<template>
  <section id="about" class="section about">
    <div class="container">
      <h2 class="section-title">Acerca de Mí</h2>
      
      <div class="about-grid">
        <div class="about-content">
          <div class="about-text">
            <p class="lead">
              Soy un profesional apasionado por la tecnología especializado en desarrollo backend y administración de sistemas.
            </p>
            
            <p>
              Con más de 4 años de experiencia, me especializo en el desarrollo de aplicaciones backend robustas y escalables utilizando Spring Boot, PHP y Laravel. Mi trayectoria en tecnología comenzó con curiosidad sobre cómo funcionan los sistemas, y ha evolucionado en una carrera dedicada a crear soluciones que realmente impacten en entornos reales.
            </p>
            
            <p>
              He creado soluciones en entornos reales como sistemas de control de asistencia y registro de visitas para instituciones públicas. Creo en escribir código limpio y mantenible, seguir buenas prácticas y estar actualizado con las tendencias de la industria. Me motiva aprender, construir y compartir conocimiento con la comunidad de desarrolladores.
            </p>

            <div class="about-highlights">
              <div class="highlight-item">
                <span class="highlight-icon">🎯</span>
                <div>
                  <h4>Enfoque</h4>
                  <p>Arquitectura escalable y optimización de infraestructura</p>
                </div>
              </div>
              
              <div class="highlight-item">
                <span class="highlight-icon">💡</span>
                <div>
                  <h4>Metodología</h4>
                  <p>Microservicios, buenas prácticas y mejora continua</p>
                </div>
              </div>
              
              <div class="highlight-item">
                <span class="highlight-icon">🚀</span>
                <div>
                  <h4>Objetivo</h4>
                  <p>Crear soluciones que generen impacto real</p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="about-stats">
          <div 
            v-for="stat in stats" 
            :key="stat.label" 
            class="stat-card"
          >
            <div class="stat-number">{{ stat.number }}</div>
            <div class="stat-label">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  background: var(--bg);
}

.about-grid {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 60px;
  align-items: start;
}

.about-text {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.lead {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--text);
  line-height: 1.6;
}

.about-text p {
  color: var(--text-secondary);
  line-height: 1.8;
  font-size: 1.125rem;
}

.about-highlights {
  display: flex;
  flex-direction: column;
  gap: 24px;
  margin-top: 32px;
}

.highlight-item {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}

.highlight-icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.highlight-item h4 {
  font-size: 1.125rem;
  font-weight: 600;
  margin-bottom: 4px;
  color: var(--text);
}

.highlight-item p {
  color: var(--text-secondary);
  font-size: 0.875rem;
  margin: 0;
}

.about-stats {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.stat-card {
  background: var(--card);
  border: 2px solid var(--border);
  border-radius: 16px;
  padding: 32px 24px;
  text-align: center;
  transition: all 0.3s ease;
}

.stat-card:hover {
  transform: translateY(-4px);
  border-color: var(--primary);
  box-shadow: 0 8px 16px rgba(10, 132, 255, 0.1);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 800;
  color: var(--primary);
  margin-bottom: 8px;
}

.stat-label {
  font-size: 0.875rem;
  color: var(--text-secondary);
  font-weight: 500;
}

@media (max-width: 1024px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .about-stats {
    grid-template-columns: repeat(4, 1fr);
  }
}

@media (max-width: 768px) {
  .about-stats {
    grid-template-columns: 1fr 1fr;
  }

  .lead {
    font-size: 1.25rem;
  }

  .about-text p {
    font-size: 1rem;
  }

  .stat-card {
    padding: 24px 16px;
  }

  .stat-number {
    font-size: 2rem;
  }
}
</style>
