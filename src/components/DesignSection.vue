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
      { duration: 0.7, delay: stagger(0.1), easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.2 })
})
</script>

<template>
  <section class="design-section">
    <div ref="sectionRef" class="section-container">
      <!-- Stacked Logo Animation -->
      <div class="logo-stack-wrapper">
        <ul class="app-logo-stack">
          <!-- Front card - Figma -->
          <li class="stack-0">
            <div class="logo-inner">
              <div class="icon-figma">
                <svg width="32" height="32" viewBox="0 0 24 24" fill="none">
                  <path d="M8 24c2.208 0 4-1.792 4-4v-4H8c-2.208 0-4 1.792-4 4s1.792 4 4 4z" fill="#0ACF83"/>
                  <path d="M4 12c0-2.208 1.792-4 4-4h4v8H8c-2.208 0-4-1.792-4-4z" fill="#A259FF"/>
                  <path d="M4 4c0-2.208 1.792-4 4-4h4v8H8C5.792 8 4 6.208 4 4z" fill="#F24E1E"/>
                  <path d="M12 0h4c2.208 0 4 1.792 4 4s-1.792 4-4 4h-4V0z" fill="#FF7262"/>
                  <path d="M20 12c0 2.208-1.792 4-4 4s-4-1.792-4-4 1.792-4 4-4 4 1.792 4 4z" fill="#1ABCFE"/>
                </svg>
              </div>
            </div>
          </li>

          <!-- Middle card - Flutter -->
          <li class="stack-1">
            <div class="logo-inner">
              <div class="icon-flutter">
                <svg width="28" height="28" viewBox="0 0 24 24" fill="#fff">
                  <path d="M14.314 0L2.3 12 6 15.7 21.684.013h-7.357L14.314 0zm.014 11.072L7.857 17.53l6.47 6.47H21.7l-6.468-6.468 6.46-6.46h-7.378z"/>
                </svg>
              </div>
            </div>
          </li>

          <!-- Back card - Tailwind -->
          <li class="stack-2">
            <div class="logo-inner">
              <div class="icon-tailwind">
                <svg width="32" height="32" viewBox="0 0 24 24" fill="#fff">
                  <path d="M12.001 4.8c-3.2 0-5.2 1.6-6 4.8 1.2-1.6 2.6-2.2 4.2-1.8.913.228 1.565.89 2.288 1.624C13.666 10.618 15.027 12 18.001 12c3.2 0 5.2-1.6 6-4.8-1.2 1.6-2.6 2.2-4.2 1.8-.913-.228-1.565-.89-2.288-1.624C16.337 6.182 14.976 4.8 12.001 4.8zm-6 7.2c-3.2 0-5.2 1.6-6 4.8 1.2-1.6 2.6-2.2 4.2-1.8.913.228 1.565.89 2.288 1.624 1.177 1.194 2.538 2.576 5.512 2.576 3.2 0 5.2-1.6 6-4.8-1.2 1.6-2.6 2.2-4.2 1.8-.913-.228-1.565-.89-2.288-1.624C10.337 13.382 8.976 12 6.001 12z"/>
                </svg>
              </div>
            </div>
          </li>
        </ul>
      </div>

      <h2 data-animate class="section-heading">From inspiration to creation.</h2>
      
      <div class="cards-row">
        <!-- Card 1: Design to Code -->
        <div data-animate class="card-wrapper">
          <div class="card card-1">
            <div class="toolbar-float">
              <button class="toolbar-btn clear-btn">Clear</button>
              <button class="toolbar-btn download-btn">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
                  <polyline points="7 10 12 15 17 10"/>
                  <line x1="12" y1="15" x2="12" y2="3"/>
                </svg>
              </button>
              <button class="toolbar-btn copy-btn">
                Copy
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <rect x="3" y="3" width="7" height="7" rx="1.5"/>
                  <rect x="14" y="3" width="7" height="7" rx="1.5"/>
                  <rect x="3" y="14" width="7" height="7" rx="1.5"/>
                  <rect x="14" y="14" width="7" height="7" rx="1.5"/>
                </svg>
              </button>
              <button class="toolbar-btn save-btn">Export</button>
            </div>
          </div>
          <div class="card-title">Design to Code</div>
          <p class="card-description">We translate your Figma designs into pixel-perfect, production-ready code with Vue, React, or Flutter.</p>
        </div>

        <!-- Card 2: Component Library -->
        <div data-animate class="card-wrapper">
          <div class="card card-2">
            <div class="save-panel">
              <div class="save-section-label">Components</div>
              <div class="save-item">
                <div class="save-item-left">
                  <div class="save-item-icon grid-icon">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#555" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <rect x="3" y="3" width="7" height="7" rx="1"/>
                      <rect x="14" y="3" width="7" height="7" rx="1"/>
                      <rect x="3" y="14" width="7" height="7" rx="1"/>
                      <rect x="14" y="14" width="7" height="7" rx="1"/>
                    </svg>
                  </div>
                  <span class="save-item-name">UI Library</span>
                </div>
                <span class="bookmark-icon">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="#1a1a1a" stroke="#1a1a1a" stroke-width="2">
                    <path d="M19 21l-7-5-7 5V5a2 2 0 0 1 2-2h10a2 2 0 0 1 2 2z"/>
                  </svg>
                </span>
              </div>

              <div class="save-divider"></div>
              <div class="save-section-label" style="margin-top:12px;">Add to project</div>

              <div class="save-item">
                <div class="save-item-left">
                  <div class="component-thumb vue">V</div>
                  <span class="save-item-name">Vue Components</span>
                </div>
                <div class="checkmark-blue">
                  <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="3" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"/>
                  </svg>
                </div>
              </div>

              <div class="save-item">
                <div class="save-item-left">
                  <div class="component-thumb flutter">F</div>
                  <span class="save-item-name">Flutter Widgets</span>
                </div>
              </div>

              <div class="save-item">
                <div class="save-item-left">
                  <div class="component-thumb tailwind">T</div>
                  <span class="save-item-name">Tailwind CSS</span>
                </div>
                <div class="checkmark-blue">
                  <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="3" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"/>
                  </svg>
                </div>
              </div>
            </div>
          </div>
          <div class="card-title">Component Library</div>
          <p class="card-description">Reusable, well-documented components that scale with your product and team.</p>
        </div>

        <!-- Card 3: Collaborative Review -->
        <div data-animate class="card-wrapper">
          <div class="card card-3">
            <div class="comment-panel">
              <div class="comment-header">
                <div class="comment-avatar">SY</div>
                <div>
                  <span class="comment-user">Simphiwe</span>
                  <span class="comment-time">2h ago</span>
                </div>
              </div>
              <div class="comment-text">
                Design looks great! Let's add a subtle hover animation to the cards.
              </div>
              <div class="comment-input-row">
                <div class="comment-input-text">
                  On it!<span class="cursor"></span>
                </div>
                <button class="send-btn">
                  <svg viewBox="0 0 24 24" fill="none" width="16" height="16">
                    <path d="M12 5l0 14" stroke="#fff" stroke-width="2.5" stroke-linecap="round"/>
                    <path d="M5 12l7-7 7 7" stroke="#fff" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </button>
              </div>
            </div>
          </div>
          <div class="card-title">Collaborative Review</div>
          <p class="card-description">Real-time feedback loops between design and development. No lost context.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.design-section {
  background: #fff;
  padding: 100px 24px;
}

.section-container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-heading {
  text-align: center;
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.5rem, 6vw, 4rem);
  font-weight: 400;
  letter-spacing: -0.02em;
  margin-bottom: 60px;
  line-height: 1.1;
  color: #1a1a1a;
}

/* Stacked Logo Animation */
.logo-stack-wrapper {
  display: flex;
  justify-content: center;
  margin-bottom: 32px;
  padding-top: 24px;
}

.app-logo-stack {
  position: relative;
  isolation: isolate;
  width: 80px;
  height: 80px;
  list-style: none;
  padding: 0;
  margin: 0;
}

.app-logo-stack li {
  position: absolute;
  inset: 0;
  overflow: hidden;
  border-radius: 20px;
  transform-origin: center top;
}

.app-logo-stack li .logo-inner {
  width: 100%;
  height: 100%;
  position: relative;
}

.app-logo-stack li .logo-inner::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 20px;
  box-shadow: inset 0 0 0 0.5px rgba(0, 0, 0, 0.1);
  pointer-events: none;
}

/* Icon backgrounds */
.icon-figma {
  width: 100%;
  height: 100%;
  background: #1e1e1e;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px;
}

.icon-flutter {
  width: 100%;
  height: 100%;
  background: #027DFD;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px;
}

.icon-tailwind {
  width: 100%;
  height: 100%;
  background: #06B6D4;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px;
}

/* Card positions */
.stack-0 { z-index: 3; }
.stack-1 { z-index: 2; transform: translateY(-8px) scale(0.82); }
.stack-2 { z-index: 1; transform: translateY(-16px) scale(0.64); }

/* Animation */
.stack-0 {
  animation: card0 8s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

.stack-1 {
  animation: card1 8s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

.stack-2 {
  animation: card2 8s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

@keyframes card0 {
  0%, 2% {
    z-index: 3;
    transform: translateY(0) scale(1);
    opacity: 1;
  }
  8% {
    transform: translateY(-30px) scale(0.95);
    opacity: 0;
    z-index: 3;
  }
  8.01% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
    opacity: 0;
  }
  12% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
    opacity: 1;
  }
  33%, 35% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
  }
  41% {
    z-index: 2;
    transform: translateY(-8px) scale(0.82);
  }
  66%, 68% {
    z-index: 2;
    transform: translateY(-8px) scale(0.82);
  }
  74% {
    z-index: 3;
    transform: translateY(0) scale(1);
  }
  100% {
    z-index: 3;
    transform: translateY(0) scale(1);
    opacity: 1;
  }
}

@keyframes card1 {
  0%, 2% {
    z-index: 2;
    transform: translateY(-8px) scale(0.82);
  }
  8% {
    z-index: 3;
    transform: translateY(0) scale(1);
  }
  33%, 35% {
    z-index: 3;
    transform: translateY(0) scale(1);
    opacity: 1;
  }
  41% {
    transform: translateY(-30px) scale(0.95);
    opacity: 0;
    z-index: 3;
  }
  41.01% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
    opacity: 0;
  }
  45% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
    opacity: 1;
  }
  66%, 68% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
  }
  74% {
    z-index: 2;
    transform: translateY(-8px) scale(0.82);
  }
  100% {
    z-index: 2;
    transform: translateY(-8px) scale(0.82);
  }
}

@keyframes card2 {
  0%, 2% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
  }
  8% {
    z-index: 2;
    transform: translateY(-8px) scale(0.82);
  }
  33%, 35% {
    z-index: 2;
    transform: translateY(-8px) scale(0.82);
  }
  41% {
    z-index: 3;
    transform: translateY(0) scale(1);
  }
  66%, 68% {
    z-index: 3;
    transform: translateY(0) scale(1);
    opacity: 1;
  }
  74% {
    transform: translateY(-30px) scale(0.95);
    opacity: 0;
    z-index: 3;
  }
  74.01% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
    opacity: 0;
  }
  78% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
    opacity: 1;
  }
  100% {
    z-index: 1;
    transform: translateY(-16px) scale(0.64);
  }
}

.cards-row {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.card-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card {
  width: 100%;
  height: 300px;
  background: #f5f5f7;
  border-radius: 20px;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 24px;
}

/* Card 1 - Design to Code */
.card-1 {
  align-items: flex-end;
  justify-content: flex-start;
  padding: 0 0 36px 24px;
}

.toolbar-float {
  display: flex;
  align-items: center;
  background: #1a1a1a;
  border-radius: 14px;
  padding: 5px;
  gap: 0;
  box-shadow: 0 8px 30px rgba(0,0,0,0.15);
}

.toolbar-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 10px 16px;
  border: none;
  background: transparent;
  color: #fff;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  border-radius: 10px;
  white-space: nowrap;
}

.toolbar-btn.clear-btn {
  background: #333;
  color: #fff;
}

.toolbar-btn.download-btn {
  padding: 10px 12px;
}

.toolbar-btn.copy-btn {
  display: flex;
  align-items: center;
  gap: 6px;
}

.toolbar-btn.save-btn {
  background: #fff;
  color: #1a1a1a;
  font-weight: 600;
}

/* Card 2 - Component Library */
.card-2 {
  padding: 24px;
}

.save-panel {
  background: #fff;
  border-radius: 16px;
  padding: 18px;
  width: 240px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.06);
}

.save-section-label {
  font-size: 11px;
  font-weight: 600;
  color: #888;
  margin-bottom: 10px;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.save-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px 4px;
  cursor: pointer;
  border-radius: 8px;
  transition: background 0.15s;
}

.save-item:hover {
  background: #f5f5f7;
}

.save-item-left {
  display: flex;
  align-items: center;
  gap: 10px;
}

.save-item-icon {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  background: #f0f0f0;
  color: #555;
}

.save-item-icon.grid-icon {
  background: transparent;
}

.save-item-name {
  font-size: 14px;
  font-weight: 500;
  color: #1a1a1a;
}

.save-divider {
  height: 1px;
  background: #eee;
  margin: 6px 0;
}

.component-thumb {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: 700;
  color: #fff;
}

.component-thumb.vue {
  background: #42b883;
}

.component-thumb.flutter {
  background: #027DFD;
}

.component-thumb.tailwind {
  background: #06B6D4;
}

.checkmark-blue {
  width: 20px;
  height: 20px;
  background: #4a90d9;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.bookmark-icon {
  font-size: 18px;
  color: #1a1a1a;
}

/* Card 3 - Collaborative Review */
.card-3 {
  padding: 24px;
}

.comment-panel {
  background: #fff;
  border-radius: 16px;
  padding: 18px;
  width: 260px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.06);
}

.comment-header {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 6px;
}

.comment-avatar {
  width: 34px;
  height: 34px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea, #764ba2);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 11px;
  font-weight: 600;
}

.comment-user {
  font-size: 14px;
  font-weight: 700;
  color: #1a1a1a;
}

.comment-time {
  font-size: 12px;
  color: #999;
  font-weight: 400;
  margin-left: 4px;
}

.comment-text {
  font-size: 13px;
  color: #333;
  line-height: 1.5;
  margin-bottom: 14px;
  margin-left: 44px;
  margin-top: -2px;
}

.comment-input-row {
  display: flex;
  align-items: center;
  gap: 8px;
  background: #f0f0f0;
  border-radius: 24px;
  padding: 8px 10px 8px 16px;
}

.comment-input-text {
  flex: 1;
  font-size: 13px;
  color: #1a1a1a;
  font-weight: 400;
}

.comment-input-text .cursor {
  display: inline-block;
  width: 1.5px;
  height: 14px;
  background: #4a90d9;
  vertical-align: middle;
  margin-left: 1px;
  animation: blink 1s infinite;
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

.send-btn {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: #4a90d9;
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  flex-shrink: 0;
}

/* Card labels */
.card-title {
  font-size: 18px;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 8px;
  text-align: center;
}

.card-description {
  font-size: 14px;
  color: #777;
  text-align: center;
  line-height: 1.5;
  max-width: 280px;
}

/* Mobile responsive */
@media (max-width: 900px) {
  .cards-row {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .card-wrapper:last-child {
    grid-column: span 2;
    max-width: 400px;
    margin: 0 auto;
  }
}

@media (max-width: 640px) {
  .design-section {
    padding: 60px 16px;
  }
  
  .section-heading {
    margin-bottom: 40px;
  }
  
  .cards-row {
    grid-template-columns: 1fr;
    gap: 32px;
  }
  
  .card-wrapper:last-child {
    grid-column: span 1;
  }
  
  .card {
    height: 260px;
  }
  
  .toolbar-float {
    transform: scale(0.9);
    transform-origin: bottom left;
  }
  
  .save-panel,
  .comment-panel {
    width: 220px;
    padding: 14px;
  }
  
  .card-title {
    font-size: 16px;
  }
  
  .card-description {
    font-size: 13px;
    max-width: 260px;
  }
}
</style>
