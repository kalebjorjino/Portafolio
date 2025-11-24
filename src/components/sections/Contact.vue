<script setup>
import { ref, reactive } from 'vue'
import Button from '../ui/Button.vue'

const form = reactive({
  name: '',
  email: '',
  message: ''
})

const errors = reactive({
  name: '',
  email: '',
  message: ''
})

const isSubmitting = ref(false)
const submitStatus = ref(null) // 'success' | 'error' | null

const validateEmail = (email) => {
  const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  return re.test(email)
}

const validateForm = () => {
  let isValid = true

  // Reset errors
  errors.name = ''
  errors.email = ''
  errors.message = ''

  // Validate name
  if (!form.name.trim()) {
    errors.name = 'El nombre es requerido'
    isValid = false
  } else if (form.name.trim().length < 2) {
    errors.name = 'El nombre debe tener al menos 2 caracteres'
    isValid = false
  }

  // Validate email
  if (!form.email.trim()) {
    errors.email = 'El email es requerido'
    isValid = false
  } else if (!validateEmail(form.email)) {
    errors.email = 'Por favor ingresa un email válido'
    isValid = false
  }

  // Validate message
  if (!form.message.trim()) {
    errors.message = 'El mensaje es requerido'
    isValid = false
  } else if (form.message.trim().length < 10) {
    errors.message = 'El mensaje debe tener al menos 10 caracteres'
    isValid = false
  }

  return isValid
}

const handleSubmit = async () => {
  submitStatus.value = null

  if (!validateForm()) {
    return
  }

  isSubmitting.value = true

  try {
    // Replace with your actual endpoint
    const response = await fetch('https://formspree.io/f/YOUR_FORM_ID', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        name: form.name,
        email: form.email,
        message: form.message
      })
    })

    if (response.ok) {
      submitStatus.value = 'success'
      // Reset form
      form.name = ''
      form.email = ''
      form.message = ''
    } else {
      submitStatus.value = 'error'
    }
  } catch (error) {
    console.error('Form submission error:', error)
    submitStatus.value = 'error'
  } finally {
    isSubmitting.value = false
    
    // Clear status after 5 seconds
    setTimeout(() => {
      submitStatus.value = null
    }, 5000)
  }
}
</script>

<template>
  <section id="contact" class="section contact">
    <div class="container">
      <h2 class="section-title">Ponte en Contacto</h2>
      
      <p class="contact-intro">
        ¿Tienes un proyecto en mente o quieres colaborar? No dudes en contactarme.
        Siempre estoy abierto a discutir nuevas oportunidades e ideas.
      </p>

      <div class="contact-content">
        <div class="contact-info">
          <h3 class="info-title">Conectemos</h3>
          <p class="info-desc">
            Estoy disponible para trabajos freelance y oportunidades a tiempo completo.
            ¡Envíame un mensaje y te responderé lo antes posible!
          </p>

          <div class="contact-methods">
            <div class="method">
              <span class="method-icon">📧</span>
              <div>
                <h4>Email</h4>
                <a href="mailto:kalebjorjino@gmail.com">20159238si@gmail.com</a>
              </div>
            </div>

            <div class="method">
              <span class="method-icon">💼</span>
              <div>
                <h4>LinkedIn</h4>
                <a href="https://linkedin.com/in/jorjino-garcia-vasquez-31b545128" target="_blank">
                  /in/jorjino-garcia-vasquez
                </a>
              </div>
            </div>

            <div class="method">
              <span class="method-icon">🐙</span>
              <div>
                <h4>GitHub</h4>
                <a href="https://github.com/kalebjorjino" target="_blank">
                  @kalebjorjino
                </a>
              </div>
            </div>

            <div class="method">
              <span class="method-icon">📍</span>
              <div>
                <h4>Ubicación</h4>
                <p>Bellavista, Callao, Perú</p>
              </div>
            </div>
          </div>
        </div>

        <form @submit.prevent="handleSubmit" class="contact-form">
          <div class="form-group">
            <label for="name" class="form-label">Nombre *</label>
            <input
              id="name"
              v-model="form.name"
              type="text"
              class="form-input"
              :class="{ 'has-error': errors.name }"
              placeholder="John Doe"
            />
            <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
          </div>

          <div class="form-group">
            <label for="email" class="form-label">Email *</label>
            <input
              id="email"
              v-model="form.email"
              type="email"
              class="form-input"
              :class="{ 'has-error': errors.email }"
              placeholder="john@example.com"
            />
            <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
          </div>

          <div class="form-group">
            <label for="message" class="form-label">Mensaje *</label>
            <textarea
              id="message"
              v-model="form.message"
              class="form-input form-textarea"
              :class="{ 'has-error': errors.message }"
              rows="6"
              placeholder="Cuéntame sobre tu proyecto..."
            ></textarea>
            <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
          </div>

          <Button 
            type="submit" 
            :disabled="isSubmitting"
            size="lg"
            class="submit-btn"
          >
            {{ isSubmitting ? 'Enviando...' : 'Enviar Mensaje' }} ✉️
          </Button>

          <div v-if="submitStatus === 'success'" class="status-message success">
            ✅ ¡Mensaje enviado exitosamente! Te responderé pronto.
          </div>

          <div v-if="submitStatus === 'error'" class="status-message error">
            ❌ ¡Oops! Algo salió mal. Por favor intenta de nuevo.
          </div>
        </form>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
  background: var(--card);
}

.contact-intro {
  text-align: center;
  color: var(--text-secondary);
  font-size: 1.125rem;
  max-width: 700px;
  margin: 0 auto 4rem;
  line-height: 1.6;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  max-width: 1000px;
  margin: 0 auto;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.info-title {
  font-size: 2rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 8px;
}

.info-desc {
  color: var(--text-secondary);
  line-height: 1.8;
  font-size: 1.125rem;
}

.contact-methods {
  display: flex;
  flex-direction: column;
  gap: 24px;
  margin-top: 16px;
}

.method {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}

.method-icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.method h4 {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 4px;
  color: var(--text);
}

.method a {
  color: var(--primary);
  text-decoration: none;
  transition: opacity 0.3s ease;
}

.method a:hover {
  opacity: 0.7;
  text-decoration: underline;
}

.method p {
  color: var(--text-secondary);
  margin: 0;
}

.contact-form {
  background: var(--bg);
  border: 2px solid var(--border);
  border-radius: 16px;
  padding: 40px;
}

.form-group {
  margin-bottom: 24px;
}

.form-label {
  display: block;
  font-weight: 600;
  margin-bottom: 8px;
  color: var(--text);
}

.form-input {
  width: 100%;
  padding: 14px 16px;
  border: 2px solid var(--border);
  border-radius: 8px;
  background: var(--card);
  color: var(--text);
  font-size: 1rem;
  font-family: inherit;
  transition: all 0.3s ease;
}

.form-input:focus {
  outline: none;
  border-color: var(--primary);
  box-shadow: 0 0 0 3px rgba(10, 132, 255, 0.1);
}

.form-input.has-error {
  border-color: #ff3b30;
}

.form-textarea {
  resize: vertical;
  min-height: 150px;
}

.error-message {
  display: block;
  color: #ff3b30;
  font-size: 0.875rem;
  margin-top: 6px;
}

.submit-btn {
  width: 100%;
}

.submit-btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.status-message {
  margin-top: 16px;
  padding: 16px;
  border-radius: 8px;
  font-weight: 500;
  text-align: center;
  animation: slideIn 0.3s ease;
}

.status-message.success {
  background: rgba(52, 199, 89, 0.1);
  color: #34c759;
  border: 2px solid #34c759;
}

.status-message.error {
  background: rgba(255, 59, 48, 0.1);
  color: #ff3b30;
  border: 2px solid #ff3b30;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 1024px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 40px;
  }
}

@media (max-width: 768px) {
  .contact-form {
    padding: 24px;
  }

  .info-title {
    font-size: 1.5rem;
  }

  .info-desc {
    font-size: 1rem;
  }
}
</style>
