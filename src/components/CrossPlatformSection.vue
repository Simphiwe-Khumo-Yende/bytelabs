<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const sectionRef = ref(null)

onMounted(() => {
  if (!sectionRef.value) return
  
  inView(sectionRef.value, () => {
    const cards = sectionRef.value.querySelectorAll('[data-animate]')
    animate(
      cards,
      { opacity: [0, 1], y: [40, 0] },
      { duration: 0.7, delay: stagger(0.15), easing: [0.25, 0.1, 0.25, 1] }
    )
    
    // Animate device icons with slight delay
    const devices = sectionRef.value.querySelectorAll('.device-icon')
    animate(
      devices,
      { opacity: [0, 1], scale: [0.8, 1] },
      { duration: 0.5, delay: stagger(0.1, { start: 0.4 }), easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.2 })
})
</script>

<template>
  <section class="cross-platform-section">
    <div ref="sectionRef" class="section-container">
      <div class="cards-container">
        <!-- Card 1: Tailored Tech Stack -->
        <div data-animate class="card">
          <h2 class="card-title">Tailored tech stack for every project</h2>
          <p class="card-description">We select the right frameworks and tools based on your product needs—performance, scalability, and maintainability.</p>

          <div class="card-1-content">
            <div class="tech-panel">
              <div class="panel-header">
                <div class="panel-header-left">
                  <svg class="panel-icon" viewBox="0 0 24 24" fill="none" stroke="#42b883" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <polygon points="12 2 2 7 12 12 22 7 12 2"/>
                    <polyline points="2 17 12 22 22 17"/>
                    <polyline points="2 12 12 17 22 12"/>
                  </svg>
                  <span class="panel-title">Project Stack</span>
                </div>
                <span class="panel-sparkle">✦</span>
              </div>

              <div class="fields-grid">
                <div class="field-group">
                  <span class="field-label">Frontend</span>
                  <span class="field-value">Vue.js + Tailwind</span>
                </div>
                <div class="field-group">
                  <span class="field-label">Backend</span>
                  <span class="field-value">Django REST</span>
                </div>
                <div class="field-group">
                  <span class="field-label">Mobile</span>
                  <span class="field-value">Flutter</span>
                </div>
                <div class="field-group">
                  <span class="field-label">Client</span>
                  <div class="field-value client-value">
                    <div class="client-icon">H</div>
                    <span class="client-text">Happay · Fintech</span>
                  </div>
                </div>

                <!-- Cursor -->
                <div class="cursor-container">
                  <svg class="cursor-arrow" viewBox="0 0 24 24" fill="#1a1a1a">
                    <path d="M5.5 3.21V20.8c0 .45.54.67.85.35l4.86-4.86a.5.5 0 0 1 .35-.15h6.87c.45 0 .67-.54.35-.85L5.85 2.35a.5.5 0 0 0-.35.86z"/>
                  </svg>
                  <div class="cursor-badge">
                    <div class="cursor-avatar"></div>
                    <span class="cursor-name">ByteLabs</span>
                  </div>
                </div>
              </div>

              <div class="panel-divider"></div>

              <div class="entry-row">
                <div class="entry-header">
                  <div class="entry-icon">H</div>
                  <span class="entry-meta">
                    <span class="entry-meta-bold">Happay</span>
                    &nbsp;· Payment Platform
                  </span>
                </div>
                <p class="entry-description">Building secure payment flows with real-time transaction monitoring and multi-currency support.</p>
                <div class="entry-status">
                  <svg class="entry-status-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <circle cx="12" cy="12" r="10"/>
                    <polyline points="12 6 12 12 16 14"/>
                  </svg>
                  In Development
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Card 2: Cross-platform development -->
        <div data-animate class="card">
          <h2 class="card-title">Build once, deploy everywhere</h2>
          <p class="card-description">From web apps to native mobile—we build cross-platform solutions that work seamlessly on any device.</p>

          <div class="card-2-content">
            <div class="device-icons">
              <!-- Flutter -->
              <div class="device-icon icon-flutter">
                <div class="icon-glow"></div>
                <div class="icon-inner">
                  <svg width="48" height="48" viewBox="0 0 256 317" fill="none">
                    <path d="M157.666 0.00012207L0 157.666L48.8674 206.534L255.4 0.00012207H157.666Z" fill="#54C5F8"/>
                    <path d="M156.6 145.399L72.2002 229.799L121.067 278.667L255.4 145.399H156.6Z" fill="#54C5F8"/>
                    <path d="M72.2002 229.8L121.067 180.933L169.934 229.8L121.067 278.667L72.2002 229.8Z" fill="#29B6F6"/>
                    <path d="M121.067 278.667L169.934 229.8L196.001 255.867L121.067 316.001V278.667Z" fill="#01579B"/>
                    <path d="M121.067 278.667L161.801 270.628L169.934 229.8L121.067 278.667Z" fill="url(#paint0_linear)"/>
                    <defs>
                      <linearGradient id="paint0_linear" x1="145.5" y1="254.233" x2="145.5" y2="278.667" gradientUnits="userSpaceOnUse">
                        <stop stop-color="#29B6F6" stop-opacity="0"/>
                        <stop offset="1" stop-color="#1565C0" stop-opacity="0.3"/>
                      </linearGradient>
                    </defs>
                  </svg>
                </div>
              </div>

              <!-- Vue -->
              <div class="device-icon icon-vue">
                <div class="icon-glow"></div>
                <div class="icon-inner">
                  <svg width="52" height="45" viewBox="0 0 261 226" fill="none">
                    <path d="M161.101 0.480469L130.877 52.3735L100.654 0.480469H0.496094L130.877 225.767L261.259 0.480469H161.101Z" fill="#41B883"/>
                    <path d="M161.101 0.480469L130.877 52.3735L100.654 0.480469H52.5742L130.877 136.124L209.18 0.480469H161.101Z" fill="#35495E"/>
                  </svg>
                </div>
              </div>

              <!-- Python -->
              <div class="device-icon icon-python">
                <div class="icon-glow"></div>
                <div class="icon-inner">
                  <svg width="44" height="44" viewBox="0 0 256 255" fill="none">
                    <defs>
                      <linearGradient id="pyYellow" x1="12.959%" y1="12.039%" x2="79.639%" y2="78.201%">
                        <stop stop-color="#387EB8" offset="0%"/>
                        <stop stop-color="#366994" offset="100%"/>
                      </linearGradient>
                      <linearGradient id="pyBlue" x1="19.128%" y1="20.579%" x2="90.742%" y2="88.429%">
                        <stop stop-color="#FFE052" offset="0%"/>
                        <stop stop-color="#FFC331" offset="100%"/>
                      </linearGradient>
                    </defs>
                    <path d="M126.916.072c-64.832 0-60.784 28.115-60.784 28.115l.072 29.128h61.868v8.745H41.631S.145 61.355.145 126.77c0 65.417 36.21 63.097 36.21 63.097h21.61v-30.356s-1.165-36.21 35.632-36.21h61.362s34.475.557 34.475-33.319V33.97S194.67.072 126.916.072zM92.802 19.66a11.12 11.12 0 0 1 11.13 11.13 11.12 11.12 0 0 1-11.13 11.13 11.12 11.12 0 0 1-11.13-11.13 11.12 11.12 0 0 1 11.13-11.13z" fill="url(#pyYellow)"/>
                    <path d="M128.757 254.126c64.832 0 60.784-28.115 60.784-28.115l-.072-29.127H127.6v-8.745h86.441s41.486 4.705 41.486-60.712c0-65.416-36.21-63.096-36.21-63.096h-21.61v30.355s1.165 36.21-35.632 36.21h-61.362s-34.475-.557-34.475 33.32v56.013s-5.235 33.897 62.518 33.897zm34.114-19.586a11.12 11.12 0 0 1-11.13-11.13 11.12 11.12 0 0 1 11.13-11.132 11.12 11.12 0 0 1 11.13 11.131 11.12 11.12 0 0 1-11.13 11.131z" fill="url(#pyBlue)"/>
                  </svg>
                </div>
              </div>

              <!-- Firebase -->
              <div class="device-icon icon-firebase">
                <div class="icon-glow"></div>
                <div class="icon-inner">
                  <svg width="36" height="48" viewBox="0 0 256 351" fill="none">
                    <defs>
                      <linearGradient id="firebaseA" x1="0%" y1="0%" x2="100%" y2="100%">
                        <stop stop-color="#FFC24A" offset="0%"/>
                        <stop stop-color="#FFA712" offset="100%"/>
                      </linearGradient>
                      <linearGradient id="firebaseB" x1="0%" y1="0%" x2="100%" y2="100%">
                        <stop stop-color="#F4BD62" offset="0%"/>
                        <stop stop-color="#DC8C28" offset="100%"/>
                      </linearGradient>
                      <linearGradient id="firebaseC" x1="0%" y1="0%" x2="100%" y2="100%">
                        <stop stop-color="#FFCB2B" offset="0%"/>
                        <stop stop-color="#FFAD00" offset="100%"/>
                      </linearGradient>
                    </defs>
                    <path d="M1.253 280.732l1.605-3.131 99.353-188.518-44.15-83.475C54.392-1.283 45.074.474 43.87 8.188L1.253 280.732z" fill="url(#firebaseA)"/>
                    <path d="M134.417 148.974l32.05-32.05-32.05-61.074c-4.042-7.697-14.692-7.697-18.584 0l-17.178 32.65v5.46l35.762 55.014z" fill="url(#firebaseB)"/>
                    <path d="M0 282.998l.962-.968 3.496-1.42 128.477-128 1.628-4.431-32.05-61.074L0 282.998z" fill="url(#firebaseC)"/>
                    <path d="M139.12 347.551l116.275-64.847-32.702-202.2c-2.46-13.156-18.988-17.588-27.562-7.39L0 282.998l115.608 64.548a24.488 24.488 0 0 0 23.512.005z" fill="#F6820C"/>
                    <path fill-opacity=".2" d="M139.12 345.64L255.395 280.79l-32.702-200.288c-2.46-13.156-18.988-17.588-27.562-7.39L0 281.086l115.608 64.548a24.488 24.488 0 0 0 23.512.005z"/>
                    <path d="M139.12 345.64L255.395 280.79l-32.702-200.288c-2.46-13.156-18.988-17.588-27.562-7.39L0 281.086l115.608 64.548a24.488 24.488 0 0 0 23.512.005z" fill="url(#firebaseC)"/>
                  </svg>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.cross-platform-section {
  background: #f5f5f7;
  padding: 80px 24px 0;
}

.section-container {
  max-width: 1200px;
  margin: 0 auto;
}

.cards-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
}

.card {
  background: #fff;
  border-radius: 24px;
  padding: 32px;
  min-height: 400px;
  position: relative;
  overflow: hidden;
}

.card-title {
  font-family: 'Inter', sans-serif;
  font-size: 22px;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 8px;
  letter-spacing: -0.3px;
}

.card-description {
  font-size: 15px;
  color: #888;
  line-height: 1.6;
  max-width: 400px;
}

/* ========== Card 1: Tech Stack ========== */
.card-1-content {
  margin-top: 32px;
  position: relative;
}

.tech-panel {
  background: #fff;
  border: 1px solid #e8e8e8;
  border-radius: 16px;
  padding: 22px;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.06);
  max-width: 400px;
}

.panel-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 18px;
}

.panel-header-left {
  display: flex;
  align-items: center;
  gap: 8px;
}

.panel-icon {
  width: 20px;
  height: 20px;
}

.panel-title {
  font-size: 15px;
  font-weight: 700;
  color: #1a1a1a;
}

.panel-sparkle {
  color: #42b883;
  font-size: 18px;
}

.fields-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px 28px;
  margin-bottom: 18px;
  position: relative;
}

.field-group {
  display: flex;
  flex-direction: column;
  gap: 3px;
}

.field-label {
  font-size: 11px;
  color: #aaa;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.03em;
}

.field-value {
  font-size: 14px;
  font-weight: 600;
  color: #1a1a1a;
}

.field-value.client-value {
  display: flex;
  align-items: center;
  gap: 8px;
}

.client-icon {
  width: 20px;
  height: 20px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 10px;
  font-weight: 700;
  flex-shrink: 0;
}

.client-text {
  font-size: 13px;
  font-weight: 500;
  color: #888;
}

/* Cursor with avatar */
.cursor-container {
  position: absolute;
  top: 32px;
  left: 190px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  z-index: 10;
}

.cursor-arrow {
  width: 18px;
  height: 18px;
  filter: drop-shadow(0 1px 2px rgba(0,0,0,0.2));
}

.cursor-badge {
  display: flex;
  align-items: center;
  gap: 4px;
  background: #42b883;
  border-radius: 10px;
  padding: 3px 8px 3px 5px;
  margin-top: -2px;
  margin-left: 10px;
  box-shadow: 0 2px 8px rgba(66, 184, 131, 0.3);
}

.cursor-avatar {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: linear-gradient(135deg, #35495e, #42b883);
  border: 1.5px solid rgba(255,255,255,0.5);
}

.cursor-name {
  font-size: 10px;
  font-weight: 600;
  color: #fff;
}

/* Divider */
.panel-divider {
  height: 1px;
  background: #eee;
  margin: 14px 0;
}

/* Bottom entry */
.entry-row {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.entry-header {
  display: flex;
  align-items: center;
  gap: 8px;
}

.entry-icon {
  width: 20px;
  height: 20px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 10px;
  font-weight: 700;
  flex-shrink: 0;
}

.entry-meta {
  font-size: 12px;
  color: #bbb;
  font-weight: 500;
}

.entry-meta-bold {
  color: #888;
  font-weight: 600;
}

.entry-description {
  font-size: 13px;
  color: #999;
  line-height: 1.5;
  padding-left: 28px;
}

.entry-status {
  display: flex;
  align-items: center;
  gap: 5px;
  padding-left: 28px;
  color: #42b883;
  font-size: 12px;
  font-weight: 500;
}

.entry-status-icon {
  width: 13px;
  height: 13px;
}

/* ========== Card 2: Cross-platform ========== */
.card-2-content {
  margin-top: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  height: 260px;
}

.device-icons {
  position: relative;
  width: 260px;
  height: 260px;
}

.device-icon {
  position: absolute;
  border-radius: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.3s ease;
  cursor: pointer;
}

.icon-inner {
  position: relative;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  border-radius: 24px;
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
}

.icon-glow {
  position: absolute;
  inset: -8px;
  border-radius: 32px;
  opacity: 0;
  transition: opacity 0.4s ease;
  z-index: 0;
  filter: blur(20px);
}

.device-icon:hover .icon-glow {
  opacity: 1;
}

.device-icon:hover {
  transform: translateY(-8px) scale(1.08);
}

.device-icon::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 24px;
  padding: 1.5px;
  background: linear-gradient(135deg, rgba(255,255,255,0.8), rgba(255,255,255,0.2));
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}

.device-icon::after {
  content: '';
  position: absolute;
  top: 4px;
  left: 12%;
  right: 12%;
  height: 40%;
  border-radius: 50%;
  background: linear-gradient(180deg, rgba(255,255,255,0.7) 0%, rgba(255,255,255,0) 100%);
  pointer-events: none;
}

/* Flutter */
.icon-flutter {
  width: 120px;
  height: 120px;
  background: linear-gradient(145deg, #e8f4ff 0%, #cce5ff 100%);
  box-shadow: 0 12px 40px rgba(2, 125, 253, 0.15), 0 4px 12px rgba(0,0,0,0.05);
  top: 0;
  left: 20px;
  z-index: 4;
  animation: float-1 6s ease-in-out infinite;
}

.icon-flutter .icon-glow {
  background: radial-gradient(circle, rgba(2, 125, 253, 0.4) 0%, transparent 70%);
}

.icon-flutter:hover {
  box-shadow: 0 20px 50px rgba(2, 125, 253, 0.25), 0 8px 20px rgba(0,0,0,0.08);
}

/* Vue */
.icon-vue {
  width: 110px;
  height: 110px;
  background: linear-gradient(145deg, #e8fff0 0%, #c8f7d6 100%);
  box-shadow: 0 12px 40px rgba(66, 184, 131, 0.15), 0 4px 12px rgba(0,0,0,0.05);
  top: 50px;
  left: 110px;
  z-index: 3;
  animation: float-2 5s ease-in-out infinite;
}

.icon-vue .icon-glow {
  background: radial-gradient(circle, rgba(66, 184, 131, 0.4) 0%, transparent 70%);
}

.icon-vue:hover {
  box-shadow: 0 20px 50px rgba(66, 184, 131, 0.25), 0 8px 20px rgba(0,0,0,0.08);
}

/* Python/Django */
.icon-python {
  width: 100px;
  height: 100px;
  background: linear-gradient(145deg, #fffbe8 0%, #fef3c7 100%);
  box-shadow: 0 12px 40px rgba(55, 118, 171, 0.12), 0 4px 12px rgba(0,0,0,0.05);
  top: 110px;
  left: 40px;
  z-index: 2;
  animation: float-3 7s ease-in-out infinite;
}

.icon-python .icon-glow {
  background: radial-gradient(circle, rgba(55, 118, 171, 0.35) 0%, transparent 70%);
}

.icon-python:hover {
  box-shadow: 0 20px 50px rgba(55, 118, 171, 0.2), 0 8px 20px rgba(0,0,0,0.08);
}

/* Firebase */
.icon-firebase {
  width: 110px;
  height: 110px;
  background: linear-gradient(145deg, #fff5eb 0%, #ffe4c4 100%);
  box-shadow: 0 12px 40px rgba(255, 160, 0, 0.15), 0 4px 12px rgba(0,0,0,0.05);
  top: 150px;
  left: 130px;
  z-index: 1;
  animation: float-4 5.5s ease-in-out infinite;
}

.icon-firebase .icon-glow {
  background: radial-gradient(circle, rgba(255, 160, 0, 0.4) 0%, transparent 70%);
}

.icon-firebase:hover {
  box-shadow: 0 20px 50px rgba(255, 160, 0, 0.25), 0 8px 20px rgba(0,0,0,0.08);
}

/* Floating animations */
@keyframes float-1 {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-12px) rotate(2deg); }
}

@keyframes float-2 {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-10px) rotate(-2deg); }
}

@keyframes float-3 {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-8px) rotate(1.5deg); }
}

@keyframes float-4 {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-14px) rotate(-1.5deg); }
}

/* Mobile responsive */
@media (max-width: 900px) {
  .cards-container {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  
  .card {
    min-height: auto;
    padding: 32px;
  }
}

@media (max-width: 640px) {
  .cross-platform-section {
    padding: 60px 16px;
  }
  
  .card {
    padding: 24px;
  }
  
  .card-title {
    font-size: 20px;
  }
  
  .card-description {
    font-size: 14px;
  }
  
  .tech-panel {
    padding: 18px;
    max-width: 100%;
  }
  
  .fields-grid {
    gap: 12px 20px;
  }
  
  .cursor-container {
    display: none;
  }
  
  .device-icons {
    width: 240px;
    height: 240px;
  }
  
  .icon-flutter {
    width: 100px;
    height: 100px;
  }
  
  .icon-vue {
    width: 90px;
    height: 90px;
    top: 40px;
    left: 95px;
  }
  
  .icon-python {
    width: 85px;
    height: 85px;
    top: 95px;
    left: 30px;
  }
  
  .icon-firebase {
    width: 95px;
    height: 95px;
    top: 130px;
    left: 110px;
  }
  
  .card-2-content {
    height: 260px;
  }
}
</style>
