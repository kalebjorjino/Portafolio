<script setup>
const currentYear = new Date().getFullYear()

const socialLinks = [
  { name: 'GitHub', icon: '🔗', url: 'https://github.com/tuusuario' },
  { name: 'LinkedIn', icon: '💼', url: 'https://linkedin.com/in/tuusuario' },
  { name: 'Twitter', icon: '🐦', url: 'https://twitter.com/tuusuario' },
  { name: 'Email', icon: '✉️', url: 'mailto:tu@email.com' }
]
</script>

<template>
  <footer class="footer">
    <div class="container footer-content">
      <div class="footer-section">
        <h3 class="footer-logo">{'<Dev />'}</h3>
        <p class="footer-text">
          Building innovative solutions with modern technologies
        </p>
      </div>

      <div class="footer-section">
        <h4 class="footer-title">Connect</h4>
        <div class="social-links">
          <a 
            v-for="link in socialLinks" 
            :key="link.name"
            :href="link.url" 
            target="_blank" 
            rel="noopener noreferrer"
            class="social-link"
            :aria-label="link.name"
          >
            <span class="social-icon">{{ link.icon }}</span>
            <span class="social-name">{{ link.name }}</span>
          </a>
        </div>
      </div>

      <div class="footer-section">
        <h4 class="footer-title">Quick Links</h4>
        <div class="quick-links">
          <a href="#about" class="footer-link">About</a>
          <a href="#skills" class="footer-link">Skills</a>
          <a href="#projects" class="footer-link">Projects</a>
          <a href="#contact" class="footer-link">Contact</a>
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <div class="container">
        <p class="copyright">
          © {{ currentYear }} 20159238si@gmail.com. Todos los derechos reservados.
        </p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--card);
  border-top: 1px solid var(--border);
  padding: 60px 0 0;
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 48px;
  padding-bottom: 48px;
}

.footer-section {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.footer-logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary);
  font-family: 'Courier New', monospace;
  margin-bottom: 8px;
}

.footer-title {
  font-size: 1.125rem;
  font-weight: 600;
  color: var(--text);
  margin-bottom: 8px;
}

.footer-text {
  color: var(--text-secondary);
  line-height: 1.6;
}

.social-links {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 12px;
  color: var(--text);
  text-decoration: none;
  transition: all 0.3s ease;
  padding: 8px;
  border-radius: 8px;
}

.social-link:hover {
  color: var(--primary);
  background: var(--bg);
  transform: translateX(4px);
}

.social-icon {
  font-size: 1.25rem;
}

.social-name {
  font-weight: 500;
}

.quick-links {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.footer-link {
  color: var(--text);
  text-decoration: none;
  transition: all 0.3s ease;
  padding: 8px;
  border-radius: 8px;
}

.footer-link:hover {
  color: var(--primary);
  background: var(--bg);
  transform: translateX(4px);
}

.footer-bottom {
  border-top: 1px solid var(--border);
  padding: 24px 0;
}

.copyright {
  text-align: center;
  color: var(--text-secondary);
  font-size: 0.875rem;
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 32px;
  }
}
</style>