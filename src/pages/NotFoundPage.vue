<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const mouseX = ref(0)
const mouseY = ref(0)

function handleMouseMove(e) {
  mouseX.value = (e.clientX / window.innerWidth - 0.5) * 20
  mouseY.value = (e.clientY / window.innerHeight - 0.5) * 20
}

onMounted(() => window.addEventListener('mousemove', handleMouseMove))
onUnmounted(() => window.removeEventListener('mousemove', handleMouseMove))
</script>

<template>
  <section class="not-found">
    <div class="not-found-content">
      <p class="not-found-label">404</p>
      <h1 class="not-found-heading">
        Page not found
      </h1>
      <p class="not-found-text">
        The page you're looking for doesn't exist or has been moved.
      </p>
      <div class="not-found-actions">
        <router-link to="/" class="not-found-btn-primary">
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" style="margin-right: 8px;">
            <path d="M10 12L6 8l4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          Back to Home
        </router-link>
        <router-link to="/contact" class="not-found-btn-secondary">
          Contact Us
        </router-link>
      </div>
    </div>

    <!-- Floating ( ) that follows cursor subtly -->
    <div
      class="not-found-ghost"
      :style="{ transform: `translate(${mouseX}px, ${mouseY}px)` }"
    >
      ( )
    </div>
  </section>
</template>

<style scoped>
.not-found {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background: #fff;
  overflow: hidden;
  padding: 40px 24px;
}

.not-found-content {
  position: relative;
  z-index: 2;
  text-align: center;
  max-width: 480px;
}

.not-found-label {
  font-family: 'Inter', sans-serif;
  font-size: 120px;
  font-weight: 800;
  letter-spacing: -4px;
  line-height: 1;
  color: #f0f0f0;
  margin: 0 0 -10px;
  user-select: none;
}

.not-found-heading {
  font-family: 'DM Serif Display', serif;
  font-size: 40px;
  font-weight: 400;
  color: #181a1c;
  margin: 0 0 16px;
  line-height: 1.2;
}

.not-found-text {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  color: #6b7280;
  line-height: 1.6;
  margin: 0 0 36px;
}

.not-found-actions {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
}

.not-found-btn-primary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 12px 28px;
  background: #181a1c;
  color: #fff;
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  font-weight: 500;
  border-radius: 50px;
  text-decoration: none;
  transition: background 0.2s;
}

.not-found-btn-primary:hover {
  background: #333;
}

.not-found-btn-secondary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 12px 28px;
  background: transparent;
  color: #181a1c;
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  font-weight: 500;
  border-radius: 50px;
  border: 1px solid #e5e7eb;
  text-decoration: none;
  transition: border-color 0.2s;
}

.not-found-btn-secondary:hover {
  border-color: #181a1c;
}

.not-found-ghost {
  position: absolute;
  z-index: 1;
  font-family: 'Inter', sans-serif;
  font-size: 240px;
  font-weight: 800;
  color: #f7f7f7;
  user-select: none;
  pointer-events: none;
  transition: transform 0.3s ease-out;
  top: 50%;
  left: 50%;
  margin-top: -120px;
  margin-left: -180px;
  line-height: 1;
}

@media (max-width: 640px) {
  .not-found-label {
    font-size: 80px;
  }
  .not-found-heading {
    font-size: 28px;
  }
  .not-found-ghost {
    font-size: 140px;
    margin-left: -100px;
    margin-top: -70px;
  }
  .not-found-actions {
    flex-direction: column;
  }
}
</style>
