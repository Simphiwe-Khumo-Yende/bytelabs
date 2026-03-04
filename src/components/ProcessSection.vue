<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const sectionRef = ref(null)

onMounted(() => {
  if (!sectionRef.value) return
  
  inView(sectionRef.value, () => {
    const items = sectionRef.value.querySelectorAll('[data-animate]')
    animate(
      items,
      { opacity: [0, 1], y: [40, 0] },
      { duration: 0.7, delay: stagger(0.12), easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.2 })
})

const steps = [
  {
    number: '01',
    title: 'Discovery',
    description: 'We dive deep into your vision, goals, and target users. Understand the problem before writing a single line of code.',
    icon: 'search',
    duration: '1-2 weeks'
  },
  {
    number: '02', 
    title: 'Design',
    description: 'Wireframes, prototypes, and high-fidelity UI. You see and approve everything before development begins.',
    icon: 'pen',
    duration: '1-2 weeks'
  },
  {
    number: '03',
    title: 'Develop',
    description: 'Agile sprints with weekly demos. Clean, tested, production-ready code delivered incrementally.',
    icon: 'code',
    duration: '4-8 weeks'
  },
  {
    number: '04',
    title: 'Deploy',
    description: 'Launch to production with CI/CD pipelines. Post-launch support and iteration based on real user feedback.',
    icon: 'rocket',
    duration: 'Ongoing'
  }
]
</script>

<template>
  <section class="process-section">
    <div ref="sectionRef" class="section-container">
      <div data-animate class="section-header">
        <span class="section-label">How We Work</span>
        <h2 class="section-heading">From idea to launch,<br>with clarity at every step.</h2>
        <p class="section-subheading">No surprises. No black boxes. You're in the loop from day one.</p>
      </div>

      <div class="process-grid">
        <div 
          v-for="(step, index) in steps" 
          :key="step.number"
          data-animate
          class="process-card"
        >
          <div class="card-header">
            <span class="step-number">{{ step.number }}</span>
            <span class="step-duration">{{ step.duration }}</span>
          </div>
          
          <div class="card-icon">
            <!-- Search/Discovery -->
            <svg v-if="step.icon === 'search'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <circle cx="11" cy="11" r="8"/>
              <path d="m21 21-4.35-4.35"/>
            </svg>
            <!-- Pen/Design -->
            <svg v-if="step.icon === 'pen'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M12 19l7-7 3 3-7 7-3-3z"/>
              <path d="M18 13l-1.5-7.5L2 2l3.5 14.5L13 18l5-5z"/>
              <path d="M2 2l7.586 7.586"/>
              <circle cx="11" cy="11" r="2"/>
            </svg>
            <!-- Code/Develop -->
            <svg v-if="step.icon === 'code'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="16 18 22 12 16 6"/>
              <polyline points="8 6 2 12 8 18"/>
            </svg>
            <!-- Rocket/Deploy -->
            <svg v-if="step.icon === 'rocket'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M4.5 16.5c-1.5 1.26-2 5-2 5s3.74-.5 5-2c.71-.84.7-2.13-.09-2.91a2.18 2.18 0 0 0-2.91-.09z"/>
              <path d="m12 15-3-3a22 22 0 0 1 2-3.95A12.88 12.88 0 0 1 22 2c0 2.72-.78 7.5-6 11a22.35 22.35 0 0 1-4 2z"/>
              <path d="M9 12H4s.55-3.03 2-4c1.62-1.08 5 0 5 0"/>
              <path d="M12 15v5s3.03-.55 4-2c1.08-1.62 0-5 0-5"/>
            </svg>
          </div>

          <h3 class="card-title">{{ step.title }}</h3>
          <p class="card-description">{{ step.description }}</p>

          <!-- Connector line -->
          <div v-if="index < steps.length - 1" class="connector-line"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.process-section {
  background: #fff;
  padding: 120px 24px;
}

.section-container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 80px;
}

.section-label {
  display: inline-block;
  font-size: 13px;
  font-weight: 600;
  color: #42b883;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 20px;
}

.section-heading {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.2rem, 5vw, 3.2rem);
  font-weight: 400;
  color: #1a1a1a;
  letter-spacing: -0.02em;
  line-height: 1.15;
  margin-bottom: 20px;
}

.section-subheading {
  font-size: 17px;
  color: #888;
  max-width: 480px;
  margin: 0 auto;
  line-height: 1.6;
}

.process-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 32px;
  position: relative;
}

.process-card {
  background: #fafafa;
  border-radius: 20px;
  padding: 32px 28px;
  position: relative;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.process-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.06);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
}

.step-number {
  font-size: 13px;
  font-weight: 700;
  color: #42b883;
  font-family: 'JetBrains Mono', monospace;
}

.step-duration {
  font-size: 11px;
  font-weight: 500;
  color: #aaa;
  background: #f0f0f0;
  padding: 4px 10px;
  border-radius: 20px;
}

.card-icon {
  width: 56px;
  height: 56px;
  background: linear-gradient(135deg, #e8fff0 0%, #d4f5e0 100%);
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  color: #42b883;
}

.card-title {
  font-size: 20px;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 12px;
  letter-spacing: -0.3px;
}

.card-description {
  font-size: 14px;
  color: #777;
  line-height: 1.65;
}

.connector-line {
  display: none;
}

/* Responsive */
@media (max-width: 1024px) {
  .process-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 24px;
  }
}

@media (max-width: 640px) {
  .process-section {
    padding: 80px 16px;
  }
  
  .process-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  
  .section-header {
    margin-bottom: 48px;
  }
}
</style>
