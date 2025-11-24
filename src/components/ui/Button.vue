<script setup>
defineProps({
  variant: {
    type: String,
    default: 'primary',
    validator: (value) => ['primary', 'secondary', 'outline'].includes(value)
  },
  size: {
    type: String,
    default: 'md',
    validator: (value) => ['sm', 'md', 'lg'].includes(value)
  }
})
</script>

<template>
  <button 
    class="btn" 
    :class="[`btn-${variant}`, `btn-${size}`]"
  >
    <slot />
  </button>
</template>

<style scoped>
.btn {
  border: none;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: inherit;
}

.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(10, 132, 255, 0.3);
}

.btn:active {
  transform: translateY(0);
}

.btn-primary {
  background: var(--primary);
  color: white;
}

.btn-secondary {
  background: var(--card);
  color: var(--text);
  border: 2px solid var(--border);
}

.btn-outline {
  background: transparent;
  color: var(--primary);
  border: 2px solid var(--primary);
}

.btn-outline:hover {
  background: var(--primary);
  color: white;
}

.btn-sm {
  padding: 8px 16px;
  font-size: 0.875rem;
}

.btn-md {
  padding: 12px 24px;
  font-size: 1rem;
}

.btn-lg {
  padding: 16px 32px;
  font-size: 1.125rem;
}
</style>