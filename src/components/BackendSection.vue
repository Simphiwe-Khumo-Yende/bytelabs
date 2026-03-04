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
      { opacity: [0, 1], y: [30, 0] },
      { duration: 0.6, delay: stagger(0.12), easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.2 })
})
</script>

<template>
  <section class="backend-section">
    <div ref="sectionRef" class="section-container">
      <div class="two-column-grid">
        <!-- Left: Workflow visualization -->
        <div data-animate class="workflow-column">
          <div class="workflow-container">
            <!-- Step 1 -->
            <div class="step-wrapper">
              <div class="step-card">
                <div class="step-header">
                  <div class="step-label-group">
                    <svg class="step-route-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <circle cx="12" cy="5" r="3"/>
                      <line x1="12" y1="8" x2="12" y2="14"/>
                      <path d="M7 19h10"/>
                      <circle cx="7" cy="19" r="2"/>
                      <circle cx="17" cy="19" r="2"/>
                      <path d="M12 14L7 17"/>
                      <path d="M12 14L17 17"/>
                    </svg>
                    <span class="step-label">API Layer</span>
                  </div>
                  <div class="step-actions">
                    <div class="step-check">
                      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                        <polyline points="20 6 9 17 4 12"/>
                      </svg>
                    </div>
                    <span class="step-dots">···</span>
                  </div>
                </div>
                <div class="step-person">
                  <div class="step-avatar avatar-django">
                    <span class="avatar-text">Dj</span>
                    <div class="avatar-online"></div>
                  </div>
                  <div>
                    <span class="step-person-name">Django REST Framework</span>
                    <span class="step-person-role">API Gateway</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- L-Connector 1 -->
            <div class="l-connector"></div>

            <!-- Step 2 -->
            <div class="step-wrapper step-indent-1">
              <div class="step-card">
                <div class="step-header">
                  <div class="step-label-group">
                    <svg class="step-route-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <circle cx="12" cy="5" r="3"/>
                      <line x1="12" y1="8" x2="12" y2="14"/>
                      <path d="M7 19h10"/>
                      <circle cx="7" cy="19" r="2"/>
                      <circle cx="17" cy="19" r="2"/>
                      <path d="M12 14L7 17"/>
                      <path d="M12 14L17 17"/>
                    </svg>
                    <span class="step-label">Business Logic</span>
                  </div>
                </div>
                <div class="step-person">
                  <div class="step-avatar avatar-python">
                    <span class="avatar-text">Py</span>
                    <div class="avatar-online"></div>
                  </div>
                  <div>
                    <span class="step-person-name">Python Services</span>
                    <span class="step-person-role">Core Processing</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- L-Connector 2 -->
            <div class="l-connector l-connector-2 step-indent-1"></div>

            <!-- Step 3 -->
            <div class="step-wrapper step-indent-2">
              <div class="step-card">
                <div class="step-header">
                  <div class="step-label-group">
                    <svg class="step-route-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <circle cx="12" cy="5" r="3"/>
                      <line x1="12" y1="8" x2="12" y2="14"/>
                      <path d="M7 19h10"/>
                      <circle cx="7" cy="19" r="2"/>
                      <circle cx="17" cy="19" r="2"/>
                      <path d="M12 14L7 17"/>
                      <path d="M12 14L17 17"/>
                    </svg>
                    <span class="step-label">Data Layer</span>
                  </div>
                </div>
                <div class="step-person">
                  <div class="step-avatar avatar-firebase">
                    <span class="avatar-text">Fb</span>
                    <div class="avatar-online"></div>
                  </div>
                  <div>
                    <span class="step-person-name">Firebase + PostgreSQL</span>
                    <span class="step-person-role">Database & Auth</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Explanation text -->
        <div data-animate class="text-column">
          <span class="section-pill">Backend Architecture</span>
          <h2 class="section-heading">Robust systems built for scale.</h2>
          <p class="section-description">
            We architect backends that handle real-world complexity—from API design to database optimization. Every layer is built with performance, security, and maintainability in mind.
          </p>
          
          <div class="features-list">
            <div class="feature-item">
              <div class="feature-icon">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
                </svg>
              </div>
              <div class="feature-text">
                <span class="feature-title">Secure by default</span>
                <span class="feature-desc">Authentication, encryption, and data protection built into every project.</span>
              </div>
            </div>
            
            <div class="feature-item">
              <div class="feature-icon">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/>
                </svg>
              </div>
              <div class="feature-text">
                <span class="feature-title">Optimized performance</span>
                <span class="feature-desc">Efficient queries, caching strategies, and load balancing for speed.</span>
              </div>
            </div>
            
            <div class="feature-item">
              <div class="feature-icon">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>
                  <line x1="8" y1="21" x2="16" y2="21"/>
                  <line x1="12" y1="17" x2="12" y2="21"/>
                </svg>
              </div>
              <div class="feature-text">
                <span class="feature-title">API-first design</span>
                <span class="feature-desc">RESTful endpoints documented and ready for any frontend or integration.</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.backend-section {
  background: #111113;
  padding: 100px 24px;
}

.section-container {
  max-width: 1200px;
  margin: 0 auto;
}

.two-column-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

/* Left column - Workflow */
.workflow-column {
  display: flex;
  justify-content: center;
}

.workflow-container {
  width: 100%;
  max-width: 420px;
  padding: 20px;
}

.step-wrapper {
  position: relative;
}

.step-indent-1 {
  margin-left: 40px;
}

.step-indent-2 {
  margin-left: 80px;
}

.step-card {
  background: #242428;
  border-radius: 16px;
  padding: 16px 18px;
  border: 1px solid rgba(255, 255, 255, 0.07);
  position: relative;
}

.step-wrapper:nth-child(1) .step-card {
  opacity: 1;
}

.step-wrapper:nth-child(3) .step-card {
  opacity: 0.8;
}

.step-wrapper:nth-child(5) .step-card {
  opacity: 0.6;
}

.step-wrapper:nth-child(3) .step-card::after,
.step-wrapper:nth-child(5) .step-card::after {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 60px;
  height: 100%;
  border-radius: 0 16px 16px 0;
  background: linear-gradient(to right, transparent, rgba(17, 17, 19, 0.5));
  pointer-events: none;
}

.step-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 12px;
}

.step-label-group {
  display: flex;
  align-items: center;
  gap: 6px;
}

.step-route-icon {
  width: 14px;
  height: 14px;
  color: rgba(255, 255, 255, 0.3);
}

.step-label {
  font-size: 12px;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.4);
}

.step-actions {
  display: flex;
  align-items: center;
  gap: 8px;
}

.step-check {
  color: #42b883;
  display: flex;
  align-items: center;
}

.step-dots {
  font-size: 16px;
  color: rgba(255, 255, 255, 0.15);
  letter-spacing: 2px;
  line-height: 1;
}

.step-person {
  display: flex;
  align-items: center;
  gap: 10px;
}

.step-avatar {
  width: 28px;
  height: 28px;
  border-radius: 8px;
  position: relative;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.avatar-text {
  font-size: 10px;
  font-weight: 700;
  color: #fff;
}

.avatar-django {
  background: linear-gradient(135deg, #092e20, #44b78b);
}

.avatar-python {
  background: linear-gradient(135deg, #3776ab, #ffd43b);
}

.avatar-firebase {
  background: linear-gradient(135deg, #f57c00, #ffca28);
}

.avatar-online {
  position: absolute;
  bottom: -2px;
  right: -2px;
  width: 8px;
  height: 8px;
  background: #22c55e;
  border-radius: 50%;
  border: 2px solid #242428;
}

.step-person-name {
  font-size: 13px;
  font-weight: 700;
  color: #e0e0e0;
}

.step-person-role {
  font-size: 12px;
  color: rgba(255, 255, 255, 0.3);
  font-weight: 400;
  margin-left: 6px;
}

/* L-shaped connectors */
.l-connector {
  position: relative;
  height: 22px;
  margin-left: 0;
}

.l-connector::before {
  content: '';
  position: absolute;
  left: 22px;
  top: 0;
  width: 2px;
  height: 100%;
  background: rgba(255, 255, 255, 0.08);
}

.l-connector::after {
  content: '';
  position: absolute;
  left: 22px;
  bottom: 0;
  width: 18px;
  height: 2px;
  background: rgba(255, 255, 255, 0.08);
}

.l-connector-2::before,
.l-connector-2::after {
  background: rgba(255, 255, 255, 0.06);
}

/* Right column - Text */
.text-column {
  padding: 20px 0;
}

.section-pill {
  display: inline-block;
  background: rgba(66, 184, 131, 0.15);
  color: #42b883;
  font-size: 13px;
  font-weight: 600;
  padding: 6px 14px;
  border-radius: 20px;
  margin-bottom: 20px;
}

.section-heading {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2rem, 4vw, 2.75rem);
  font-weight: 400;
  color: #fff;
  line-height: 1.15;
  margin-bottom: 16px;
}

.section-description {
  font-size: 16px;
  color: rgba(255, 255, 255, 0.6);
  line-height: 1.7;
  margin-bottom: 36px;
  max-width: 480px;
}

.features-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.feature-item {
  display: flex;
  gap: 14px;
  align-items: flex-start;
}

.feature-icon {
  width: 40px;
  height: 40px;
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.05);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  color: #42b883;
}

.feature-text {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.feature-title {
  font-size: 15px;
  font-weight: 600;
  color: #e0e0e0;
}

.feature-desc {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.45);
  line-height: 1.5;
}

/* Mobile responsive */
@media (max-width: 900px) {
  .two-column-grid {
    grid-template-columns: 1fr;
    gap: 48px;
  }
  
  .workflow-column {
    order: 2;
  }
  
  .text-column {
    order: 1;
    text-align: center;
  }
  
  .section-description {
    margin-left: auto;
    margin-right: auto;
  }
  
  .features-list {
    align-items: center;
  }
  
  .feature-item {
    max-width: 360px;
  }
}

@media (max-width: 640px) {
  .backend-section {
    padding: 60px 16px;
  }
  
  .workflow-container {
    padding: 10px;
  }
  
  .step-indent-1 {
    margin-left: 28px;
  }
  
  .step-indent-2 {
    margin-left: 56px;
  }
  
  .step-card {
    padding: 14px 16px;
  }
  
  .step-person-name {
    font-size: 12px;
  }
  
  .step-person-role {
    font-size: 11px;
  }
  
  .section-heading {
    font-size: 1.75rem;
  }
  
  .section-description {
    font-size: 15px;
  }
  
  .feature-item {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
}
</style>
