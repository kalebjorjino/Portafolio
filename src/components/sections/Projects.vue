<script setup>
import { ref } from 'vue'
import { projects } from '../../data/projects'
import ProjectCard from '../ui/ProjectCard.vue'

const selectedFilter = ref('all')

const filters = ['all', 'Spring Boot', 'PHP', 'Laravel', 'MySQL']

const filteredProjects = ref(projects)

const filterProjects = (filter) => {
  selectedFilter.value = filter
  
  if (filter === 'all') {
    filteredProjects.value = projects
  } else {
    filteredProjects.value = projects.filter(project => 
      project.tags.includes(filter)
    )
  }
}
</script>

<template>
  <section id="projects" class="section projects">
    <div class="container">
      <h2 class="section-title">Proyectos Destacados</h2>
      
      <p class="projects-intro">
        Aquí hay algunos de mis proyectos recientes que muestran mis habilidades y experiencia 
        en la construcción de aplicaciones backend robustas y escalables.
      </p>

      <div class="filters">
        <button
          v-for="filter in filters"
          :key="filter"
          class="filter-btn"
          :class="{ active: selectedFilter === filter }"
          @click="filterProjects(filter)"
        >
          {{ filter }}
        </button>
      </div>

      <div class="projects-grid">
        <ProjectCard 
          v-for="project in filteredProjects" 
          :key="project.id"
          :project="project"
        />
      </div>

      <div v-if="filteredProjects.length === 0" class="no-projects">
        <p>No se encontraron proyectos para este filtro. ¡Intenta seleccionar otro!</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects {
  background: var(--bg);
}

.projects-intro {
  text-align: center;
  color: var(--text-secondary);
  font-size: 1.125rem;
  max-width: 700px;
  margin: 0 auto 3rem;
  line-height: 1.6;
}

.filters {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.filter-btn {
  padding: 12px 24px;
  border: 2px solid var(--border);
  background: var(--card);
  color: var(--text);
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  font-family: inherit;
}

.filter-btn:hover {
  border-color: var(--primary);
  transform: translateY(-2px);
}

.filter-btn.active {
  background: var(--primary);
  color: white;
  border-color: var(--primary);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 32px;
  animation: fadeIn 0.6s ease-out;
}

.no-projects {
  text-align: center;
  padding: 60px 20px;
  color: var(--text-secondary);
  font-size: 1.125rem;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
    gap: 24px;
  }

  .filter-btn {
    padding: 10px 20px;
    font-size: 0.875rem;
  }
}
</style>
