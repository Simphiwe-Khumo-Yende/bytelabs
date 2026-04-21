<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const sectionRef = ref(null)
const aiCardRef = ref(null)

const services = [
  {
    title: 'Vue.js & Tailwind CSS',
    description: 'Component-driven UI with utility-first styling for rapid iteration and pixel-perfect design.'
  },
  {
    title: 'Django backend',
    description: 'Python-powered APIs with built-in security, admin panels, ORM for robust data management.'
  },
  {
    title: 'Flutter & Dart',
    description: 'Single codebase for iOS and Android with native performance. Beautiful, responsive UIs with hot reload.'
  },
  {
    title: 'Firebase integration',
    description: 'Real-time databases, authentication, and cloud functions. Ship faster with managed infrastructure.'
  },
  {
    title: 'System architecture',
    description: 'Scalable designs using microservices, queues, and event-driven patterns that grow with your business.'
  },
  {
    title: 'API development',
    description: 'RESTful and GraphQL APIs built for performance, developer experience, and seamless third-party integrations.'
  }
]

const examples = [
  { text: 'Build a smart chatbot for our support team', icon: 'chat' },
  { text: 'Add AI recommendations to our e-commerce app', icon: 'cart' },
  { text: 'Automate document processing with LLMs', icon: 'doc' },
  { text: 'Create an agentic workflow for data analysis', icon: 'code' }
]

const typedText = ref('')
const fullPrompt = 'Integrate an AI agent that handles customer onboarding automatically...'
let typingTimeout = null
let restartTimeout = null

function startTypingDemo() {
  typedText.value = ''
  let i = 0
  function typeChar() {
    if (i < fullPrompt.length) {
      typedText.value = fullPrompt.slice(0, i + 1)
      i++
      typingTimeout = setTimeout(typeChar, 40)
    } else {
      restartTimeout = setTimeout(() => startTypingDemo(), 3000)
    }
  }
  typingTimeout = setTimeout(typeChar, 800)
}

function stopTypingDemo() {
  clearTimeout(typingTimeout)
  clearTimeout(restartTimeout)
}

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

  if (aiCardRef.value) {
    inView(aiCardRef.value, () => {
      startTypingDemo()
      return () => stopTypingDemo()
    }, { amount: 0.2 })
  }
})

onUnmounted(() => stopTypingDemo())
</script>

<template>
  <section id="services" class="services-section">
    <div ref="sectionRef" class="section-container">
      <div data-animate class="section-header">
        <span class="section-label">Services</span>
        <h2 class="section-heading">Everything you need<br>to ship great software.</h2>
        <p class="section-subheading">Full-stack development from frontend to backend, web to mobile.</p>
      </div>

      <div class="services-grid">
        <div
          v-for="service in services"
          :key="service.title"
          data-animate
          class="service-card"
        >
          <h3 class="card-title">{{ service.title }}</h3>
          <p class="card-description">{{ service.description }}</p>
        </div>
      </div>

      <!-- AI Integrations showcase -->
      <div ref="aiCardRef" data-animate class="ai-showcase">
        <div class="ai-showcase-inner">
          <!-- AI Mode pill -->
          <div class="ai-pill">
            <div class="ai-pill-blur"><div class="ai-pill-gradient"></div></div>
            <div class="ai-pill-border"><div class="ai-pill-gradient"></div></div>
            <div class="ai-pill-bg"></div>
            <div class="ai-pill-content">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
                <path d="M17.5 12c0-3.04 2.46-5.5 5.5-5.5-3.04 0-5.5-2.46-5.5-5.5 0 3.04-2.46 5.5-5.5 5.5 3.04 0 5.5 2.46 5.5 5.5z"/>
              </svg>
              <span>AI Mode</span>
            </div>
          </div>

          <!-- Greeting -->
          <div class="ai-greeting">
            <h3>Custom AI Integrations</h3>
            <p>What should we <span>build for you?</span></p>
          </div>

          <!-- Input card -->
          <div class="ai-input-card">
            <div class="ai-input-row">
              <span class="ai-input-icon">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M12 3L14.5 8.5L20 9L16 13.5L17 19L12 16L7 19L8 13.5L4 9L9.5 8.5L12 3Z"/>
                </svg>
              </span>
              <div class="ai-input-text">
                <span class="ai-typed-text">{{ typedText }}</span>
                <span class="ai-cursor" v-if="typedText.length < fullPrompt.length">|</span>
              </div>
            </div>
            <div class="ai-input-controls">
              <div class="ai-controls-left">
                <span class="ai-control-btn">
                  <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21.44 11.05l-9.19 9.19a6 6 0 01-8.49-8.49l9.19-9.19a4 4 0 015.66 5.66l-9.2 9.19a2 2 0 01-2.83-2.83l8.49-8.48"/></svg>
                  Attach
                </span>
              </div>
              <div class="ai-send-btn">
                <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M2.01 21L23 12 2.01 3 2 10l15 2-15 2z"/></svg>
              </div>
            </div>
          </div>

          <!-- Example cards -->
          <div class="ai-examples">
            <div class="ai-examples-label">Get started with an example</div>
            <div class="ai-examples-grid">
              <div v-for="ex in examples" :key="ex.text" class="ai-example-card">
                <p>{{ ex.text }}</p>
                <span class="ai-example-icon">
                  <svg v-if="ex.icon === 'chat'" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/></svg>
                  <svg v-if="ex.icon === 'cart'" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 002 1.61h9.72a2 2 0 002-1.61L23 6H6"/></svg>
                  <svg v-if="ex.icon === 'doc'" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>
                  <svg v-if="ex.icon === 'code'" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services-section {
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

.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
}

.service-card {
  background: #fafafa;
  border-radius: 20px;
  padding: 32px 28px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.service-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.06);
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

@media (max-width: 1024px) {
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 24px;
  }
}

@media (max-width: 640px) {
  .services-section {
    padding: 80px 16px;
  }

  .services-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }

  .section-header {
    margin-bottom: 48px;
  }
}

/* ── AI Showcase ── */
.ai-showcase {
  margin-top: 48px;
  background: #111113;
  border-radius: 24px;
  padding: 56px 40px;
  overflow: hidden;
  position: relative;
}

.ai-showcase::before {
  content: '';
  position: absolute;
  top: -100px;
  left: 50%;
  transform: translateX(-50%);
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(66, 184, 131, 0.06) 0%, transparent 60%);
  pointer-events: none;
}

.ai-showcase-inner {
  max-width: 580px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 24px;
}

/* ── AI Pill Button ── */
.ai-pill {
  position: relative;
  height: 36px;
  padding: 0 14px 0 12px;
  border-radius: 100px;
  background: #2c303d;
  overflow: visible;
}

.ai-pill-blur {
  overflow: hidden;
  border-radius: 100px;
  position: absolute;
  inset: 0;
  pointer-events: none;
  opacity: 0.35;
  filter: blur(3px);
}

.ai-pill-border {
  overflow: hidden;
  border-radius: 100px;
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.ai-pill-gradient {
  background: conic-gradient(
    rgba(49, 134, 255, 0) 0deg,
    #34a853 43deg,
    #ffd314 65deg,
    #ff4641 105deg,
    #3186ff 144deg,
    #3186ff 180deg,
    rgba(49, 134, 255, 0) 324deg,
    rgba(49, 134, 255, 0) 360deg
  );
  height: 200%;
  top: -50%;
  right: 0;
  bottom: 0;
  left: 0;
  position: absolute;
  scale: 2 1;
  animation: pill-rotate 2s linear infinite;
}

@keyframes pill-rotate {
  from { transform: rotate(180deg); }
  to { transform: rotate(540deg); }
}

.ai-pill-bg {
  position: absolute;
  inset: 2px;
  border-radius: 100px;
  background: #2c303d;
  filter: blur(3px);
}

.ai-pill-bg::after {
  content: '';
  position: absolute;
  inset: -10px;
  border-radius: 100px;
  background: #2c303d;
  opacity: 0.5;
}

.ai-pill-content {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  gap: 6px;
  height: 36px;
  color: #e8e8e8;
  font-size: 14px;
  font-weight: 400;
  line-height: 20px;
}

/* ── Greeting ── */
.ai-greeting {
  text-align: center;
}

.ai-greeting h3 {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(1.5rem, 3vw, 2rem);
  font-weight: 400;
  color: #fff;
  letter-spacing: -0.02em;
  margin-bottom: 6px;
}

.ai-greeting p {
  font-size: clamp(1.5rem, 3vw, 2rem);
  font-weight: 400;
  color: rgba(255, 255, 255, 0.4);
  font-family: 'DM Serif Display', serif;
}

.ai-greeting p span {
  color: rgba(255, 255, 255, 0.4);
}

/* ── Input Card ── */
.ai-input-card {
  width: 100%;
  background: #1e1f23;
  border-radius: 16px;
  padding: 16px;
  border: 1px solid rgba(255, 255, 255, 0.06);
}

.ai-input-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 14px;
  min-height: 28px;
}

.ai-input-icon {
  color: rgba(255, 255, 255, 0.3);
  flex-shrink: 0;
  display: flex;
}

.ai-input-text {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.5;
}

.ai-typed-text {
  white-space: pre-wrap;
}

.ai-cursor {
  color: #42b883;
  animation: cursor-blink 0.6s step-end infinite;
  font-weight: 300;
}

@keyframes cursor-blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.ai-input-controls {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.ai-controls-left {
  display: flex;
  gap: 8px;
}

.ai-control-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 6px 12px;
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  font-size: 12px;
  color: rgba(255, 255, 255, 0.5);
}

.ai-send-btn {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(255, 255, 255, 0.5);
}

/* ── Example Cards ── */
.ai-examples {
  width: 100%;
}

.ai-examples-label {
  font-size: 10px;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.25);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 12px;
}

.ai-examples-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.ai-example-card {
  background: #1e1f23;
  border-radius: 12px;
  padding: 14px;
  border: 1px solid rgba(255, 255, 255, 0.04);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 90px;
  transition: border-color 0.2s ease;
}

.ai-example-card:hover {
  border-color: rgba(255, 255, 255, 0.1);
}

.ai-example-card p {
  font-size: 12px;
  color: rgba(255, 255, 255, 0.55);
  line-height: 1.45;
  margin-bottom: 10px;
}

.ai-example-icon {
  color: rgba(255, 255, 255, 0.2);
}

/* ── AI Responsive ── */
@media (max-width: 768px) {
  .ai-showcase {
    padding: 40px 24px;
  }

  .ai-examples-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .ai-showcase {
    padding: 32px 16px;
  }

  .ai-examples-grid {
    grid-template-columns: 1fr 1fr;
    gap: 8px;
  }

  .ai-example-card {
    min-height: 80px;
    padding: 12px;
  }
}
</style>
