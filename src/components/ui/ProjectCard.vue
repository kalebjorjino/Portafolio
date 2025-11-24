<script setup>
defineProps({
  project: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="project-card">
    <div class="project-image">
      <img :src="project.image" :alt="project.title" />
      <div class="project-overlay">
        <div class="project-links">
          <a :href="project.url" target="_blank" rel="noopener noreferrer" class="project-link">
            ⚙️ Backend Code
          </a>
          <a :href="project.demo" target="_blank" rel="noopener noreferrer" class="project-link">
            🔗 API Docs
          </a>
        </div>
      </div>
    </div>
    <div class="project-content">
      <h3 class="project-title">{{ project.title }}</h3>
      <p class="project-description">{{ project.description }}</p>
      <div class="project-tags">
        <span v-for="tag in project.tags" :key="tag" class="tag">
          {{ tag }}
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.project-card {
  background: var(--card);
  border-radius: 16px;
  overflow: hidden;
  transition: all 0.3s ease;
  border: 1px solid var(--border);
  height: 100%;
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(10, 132, 255, 0.15);
}

.project-image {
  position: relative;
  width: 100%;
  height: 240px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.project-card:hover .project-image img {
  transform: scale(1.1);
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-links {
  display: flex;
  gap: 16px;
}

.project-link {
  padding: 12px 24px;
  background: var(--primary);
  color: white;
  text-decoration: none;
  border-radius: 8px;
  font-weight: 600;
  transition: all 0.3s ease;
}

.project-link:hover {
  background: white;
  color: var(--primary);
  transform: scale(1.05);
}

.project-content {
  padding: 24px;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.project-title {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 12px;
  color: var(--text);
}

.project-description {
  color: var(--text-secondary);
  margin-bottom: 16px;
  line-height: 1.6;
  flex: 1;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.tag {
  padding: 6px 12px;
  background: var(--primary);
  color: white;
  border-radius: 6px;
  font-size: 0.875rem;
  font-weight: 500;
}

@media (max-width: 768px) {
  .project-image {
    height: 200px;
  }
  
  .project-link {
    padding: 8px 16px;
    font-size: 0.875rem;
  }
}
</style>