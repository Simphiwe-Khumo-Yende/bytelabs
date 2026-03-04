<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const sectionRef = ref(null)
const counters = ref([0, 0, 0, 0])

const stats = [
  { value: 3, suffix: '+', label: 'Projects Delivered', description: 'Web & mobile apps shipped' },
  { value: 6, suffix: ' weeks', label: 'Avg. Delivery', description: 'From kickoff to launch' },
  { value: 100, suffix: '%', label: 'Client Retention', description: 'They come back for more' },
  { value: 24, suffix: '/7', label: 'Support', description: 'Post-launch assistance' }
]

function animateCounter(index, target) {
  const duration = 2000
  const start = Date.now()
  
  function update() {
    const elapsed = Date.now() - start
    const progress = Math.min(elapsed / duration, 1)
    // Ease out cubic
    const eased = 1 - Math.pow(1 - progress, 3)
    counters.value[index] = Math.round(target * eased)
    
    if (progress < 1) {
      requestAnimationFrame(update)
    }
  }
  update()
}

onMounted(() => {
  if (!sectionRef.value) return
  
  inView(sectionRef.value, () => {
    const items = sectionRef.value.querySelectorAll('[data-animate]')
    animate(
      items,
      { opacity: [0, 1], y: [30, 0] },
      { duration: 0.6, delay: stagger(0.1), easing: [0.25, 0.1, 0.25, 1] }
    )
    
    // Animate counters
    stats.forEach((stat, index) => {
      setTimeout(() => animateCounter(index, stat.value), index * 150)
    })
  }, { amount: 0.3 })
})
</script>

<template>
  <section class="stats-section">
    <div ref="sectionRef" class="section-container">
      <div class="stats-grid">
        <div 
          v-for="(stat, index) in stats" 
          :key="stat.label"
          data-animate
          class="stat-card"
        >
          <div class="stat-value">
            {{ counters[index] }}<span class="stat-suffix">{{ stat.suffix }}</span>
          </div>
          <div class="stat-label">{{ stat.label }}</div>
          <div class="stat-description">{{ stat.description }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.stats-section {
  background: #1a1a1a;
  padding: 80px 24px;
}

.section-container {
  max-width: 1200px;
  margin: 0 auto;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px;
}

.stat-card {
  text-align: center;
  position: relative;
}

.stat-card:not(:last-child)::after {
  content: '';
  position: absolute;
  right: -20px;
  top: 50%;
  transform: translateY(-50%);
  width: 1px;
  height: 60px;
  background: rgba(255, 255, 255, 0.1);
}

.stat-value {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.5rem, 5vw, 3.5rem);
  font-weight: 400;
  color: #fff;
  letter-spacing: -0.02em;
  line-height: 1;
  margin-bottom: 12px;
}

.stat-suffix {
  color: #42b883;
}

.stat-label {
  font-size: 15px;
  font-weight: 600;
  color: #fff;
  margin-bottom: 6px;
  letter-spacing: -0.2px;
}

.stat-description {
  font-size: 13px;
  color: rgba(255, 255, 255, 0.5);
}

/* Responsive */
@media (max-width: 900px) {
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 48px 40px;
  }
  
  .stat-card:nth-child(2)::after {
    display: none;
  }
  
  .stat-card:not(:last-child)::after {
    display: none;
  }
}

@media (max-width: 480px) {
  .stats-section {
    padding: 60px 16px;
  }
  
  .stats-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }
}
</style>
