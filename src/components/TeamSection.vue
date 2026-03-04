<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const sectionRef = ref(null)

const team = [
  {
    name: 'Simphiwe Yende',
    role: 'Founder & Lead Developer',
    bio: 'Full-stack engineer with a passion for clean code and beautiful interfaces. Leads architecture and development across all ByteLabs projects.',
    initials: 'SY',
    color: 'linear-gradient(135deg, #42b883 0%, #35495e 100%)'
  },
  // Add more team members as ByteLabs grows
]

const values = [
  {
    title: 'Quality First',
    description: 'We write code we\'re proud of. Every line is tested, reviewed, and built to last.',
    icon: 'star'
  },
  {
    title: 'Transparent Process',
    description: 'No surprises. Weekly updates, clear timelines, and open communication.',
    icon: 'eye'
  },
  {
    title: 'Long-term Partners',
    description: 'We don\'t just ship and disappear. We build relationships and support your growth.',
    icon: 'handshake'
  }
]

onMounted(() => {
  if (!sectionRef.value) return
  
  inView(sectionRef.value, () => {
    const items = sectionRef.value.querySelectorAll('[data-animate]')
    animate(
      items,
      { opacity: [0, 1], y: [40, 0] },
      { duration: 0.7, delay: stagger(0.1), easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.2 })
})
</script>

<template>
  <section class="team-section">
    <div ref="sectionRef" class="section-container">
      <div data-animate class="section-header">
        <span class="section-label">About ByteLabs</span>
        <h2 class="section-heading">Small team. Big impact.</h2>
        <p class="section-subheading">We're a focused team of developers and designers based in Pretoria, South Africa. We build software that matters.</p>
      </div>

      <!-- Team members -->
      <div class="team-grid">
        <div 
          v-for="member in team" 
          :key="member.name"
          data-animate
          class="team-card"
        >
          <div class="member-avatar" :style="{ background: member.color }">
            {{ member.initials }}
          </div>
          <h3 class="member-name">{{ member.name }}</h3>
          <span class="member-role">{{ member.role }}</span>
          <p class="member-bio">{{ member.bio }}</p>
          
          <div class="member-links">
            <a href="https://github.com/bytelabs" target="_blank" class="social-link">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
              </svg>
            </a>
            <a href="https://linkedin.com/in/simphiwe-khumo" target="_blank" class="social-link">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
              </svg>
            </a>
          </div>
        </div>
      </div>

      <!-- Values -->
      <div class="values-section">
        <h3 data-animate class="values-heading">What we stand for</h3>
        <div class="values-grid">
          <div 
            v-for="value in values" 
            :key="value.title"
            data-animate
            class="value-card"
          >
            <div class="value-icon">
              <svg v-if="value.icon === 'star'" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/>
              </svg>
              <svg v-if="value.icon === 'eye'" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/>
                <circle cx="12" cy="12" r="3"/>
              </svg>
              <svg v-if="value.icon === 'handshake'" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M20.42 4.58a5.4 5.4 0 0 0-7.65 0l-.77.78-.77-.78a5.4 5.4 0 0 0-7.65 0C1.46 6.7 1.33 10.28 4 13l8 8 8-8c2.67-2.72 2.54-6.3.42-8.42z"/>
              </svg>
            </div>
            <h4 class="value-title">{{ value.title }}</h4>
            <p class="value-description">{{ value.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.team-section {
  background: #fff;
  padding: 60px 24px 100px;
}

.section-container {
  max-width: 1100px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 64px;
}

.section-label {
  display: inline-block;
  font-size: 13px;
  font-weight: 600;
  color: #42b883;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 16px;
}

.section-heading {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.2rem, 5vw, 3rem);
  font-weight: 400;
  color: #1a1a1a;
  letter-spacing: -0.02em;
  margin-bottom: 16px;
}

.section-subheading {
  font-size: 17px;
  color: #888;
  max-width: 520px;
  margin: 0 auto;
  line-height: 1.6;
}

/* Team grid */
.team-grid {
  display: flex;
  justify-content: center;
  margin-bottom: 80px;
}

.team-card {
  background: #fafafa;
  border-radius: 24px;
  padding: 48px 40px;
  text-align: center;
  max-width: 380px;
}

.member-avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 28px;
  font-weight: 700;
  margin: 0 auto 24px;
}

.member-name {
  font-size: 22px;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 6px;
}

.member-role {
  font-size: 14px;
  color: #42b883;
  font-weight: 500;
  display: block;
  margin-bottom: 16px;
}

.member-bio {
  font-size: 14px;
  color: #777;
  line-height: 1.7;
  margin-bottom: 24px;
}

.member-links {
  display: flex;
  justify-content: center;
  gap: 12px;
}

.social-link {
  width: 40px;
  height: 40px;
  border-radius: 10px;
  background: #eee;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #666;
  transition: all 0.2s ease;
}

.social-link:hover {
  background: #1a1a1a;
  color: #fff;
}

/* Values */
.values-section {
  padding-top: 60px;
  border-top: 1px solid #eee;
}

.values-heading {
  font-family: 'DM Serif Display', serif;
  font-size: 24px;
  font-weight: 400;
  color: #1a1a1a;
  text-align: center;
  margin-bottom: 48px;
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
}

.value-card {
  text-align: center;
  padding: 32px 24px;
}

.value-icon {
  width: 56px;
  height: 56px;
  background: #f5f5f7;
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 20px;
  color: #42b883;
}

.value-title {
  font-size: 17px;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 10px;
}

.value-description {
  font-size: 14px;
  color: #888;
  line-height: 1.6;
}

/* Responsive */
@media (max-width: 768px) {
  .team-section {
    padding: 80px 16px;
  }
  
  .values-grid {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  
  .team-card {
    padding: 40px 24px;
  }
}
</style>
