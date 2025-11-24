<script setup>
import { skills } from '../../data/skills'
</script>

<template>
  <section id="skills" class="section skills">
    <div class="container">
      <h2 class="section-title">Habilidades y Tecnologías</h2>
      
      <p class="skills-intro">
        Trabajo con un conjunto diverso de tecnologías para construir aplicaciones backend robustas y escalables.
        Aquí hay algunas de las herramientas y frameworks en los que soy competente:
      </p>

      <div class="skills-grid">
        <div 
          v-for="skill in skills" 
          :key="skill.id" 
          class="skill-card"
          :style="{ '--skill-color': skill.color }"
        >
          <div class="skill-icon">{{ skill.icon }}</div>
          <div class="skill-name">{{ skill.name }}</div>
        </div>
      </div>

      <div class="skills-categories">
        <div class="category">
          <h3 class="category-title">Backend</h3>
          <p class="category-desc">
            Spring Boot, Spring Security, Spring Cloud, PHP, Laravel, REST APIs
          </p>
        </div>

        <div class="category">
          <h3 class="category-title">Bases de Datos</h3>
          <p class="category-desc">
            MySQL, PostgreSQL, Transact-SQL (T-SQL), Diseño de esquemas, Optimización
          </p>
        </div>

        <div class="category">
          <h3 class="category-title">DevOps & Infraestructura</h3>
          <p class="category-desc">
            Docker, Linux, Proxmox, Hyper-V, Administración de Sistemas, Git
          </p>
        </div>

        <div class="category">
          <h3 class="category-title">Otros</h3>
          <p class="category-desc">
            Microservicios, Postman, Testing, Gestión de Incidentes, Análisis de Sistemas
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills {
  background: var(--card);
}

.skills-intro {
  text-align: center;
  color: var(--text-secondary);
  font-size: 1.125rem;
  max-width: 700px;
  margin: 0 auto 4rem;
  line-height: 1.6;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
  gap: 24px;
  margin-bottom: 60px;
}

.skill-card {
  background: var(--bg);
  border: 2px solid var(--border);
  border-radius: 16px;
  padding: 32px 24px;
  text-align: center;
  transition: all 0.3s ease;
  cursor: pointer;
}

.skill-card:hover {
  transform: translateY(-8px) scale(1.05);
  border-color: var(--skill-color);
  box-shadow: 0 12px 24px rgba(10, 132, 255, 0.15);
}

.skill-icon {
  font-size: 3rem;
  margin-bottom: 12px;
  animation: float 3s ease-in-out infinite;
}

.skill-card:nth-child(even) .skill-icon {
  animation-delay: 1s;
}

.skill-name {
  font-size: 1rem;
  font-weight: 600;
  color: var(--text);
}

.skills-categories {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 32px;
  margin-top: 60px;
}

.category {
  background: var(--bg);
  border: 2px solid var(--border);
  border-radius: 16px;
  padding: 32px;
  transition: all 0.3s ease;
}

.category:hover {
  border-color: var(--primary);
  transform: translateY(-4px);
}

.category-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--primary);
  margin-bottom: 12px;
}

.category-desc {
  color: var(--text-secondary);
  line-height: 1.8;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

@media (max-width: 768px) {
  .skills-grid {
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 16px;
  }

  .skill-card {
    padding: 24px 16px;
  }

  .skill-icon {
    font-size: 2rem;
  }

  .skill-name {
    font-size: 0.875rem;
  }

  .skills-categories {
    grid-template-columns: 1fr;
    gap: 24px;
  }

  .category {
    padding: 24px;
  }
}
</style>
