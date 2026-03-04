<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger } from 'motion'
import gaiosophyLogo from '../assets/gaiosophy logo.png'
import strikepointLogo from '../assets/strikepoint logo.png'
import happayLogo from '../assets/happay logo.png'

const heroRef = ref(null)

onMounted(() => {
  if (!heroRef.value) return
  const items = heroRef.value.querySelectorAll('[data-hero]')
  animate(
    items,
    { opacity: [0, 1], y: [30, 0] },
    { duration: 0.8, delay: stagger(0.12, { start: 0.3 }), easing: [0.25, 0.1, 0.25, 1] }
  )
})
</script>

<template>
  <section style="background-color: #f5f5f7; padding-top: 96px; padding-bottom: 0; overflow: hidden;">
    <div ref="heroRef" style="max-width: 1100px; margin-left: auto; margin-right: auto; padding-left: 24px; padding-right: 24px;">
      <!-- Announcement pill -->
      <div data-hero style="opacity:0; display: flex; justify-content: center; margin-bottom: 48px;">
        <a href="#work" style="display: inline-flex; align-items: center; gap: 8px; padding: 6px 16px; border-radius: 36px; border: 1px solid rgba(24,26,28,0.1); font-size: 13px; color: rgba(24,26,28,0.7); text-decoration: none;">
          ByteLabs now building Happay — our in-house fintech product
          <svg width="10" height="10" viewBox="0 0 24 24" fill="none" style="opacity: 0.6;">
            <path d="M7 17L17 7M17 7H7M17 7v10" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </a>
      </div>

      <!-- Serif heading -->
      <h1
        data-hero
        style="opacity:0; text-align: center; font-family: 'DM Serif Display', serif; font-size: clamp(3rem, 8vw, 5.2rem); font-weight: 400; line-height: 1.05; letter-spacing: -0.02em; color: #181a1c; max-width: 900px; margin-left: auto; margin-right: auto; margin-bottom: 32px;"
      >
        Custom software, web apps, and mobile products
      </h1>

      <!-- Subtitle -->
      <p
        data-hero
        style="opacity:0; text-align: center; font-size: 17px; color: rgba(24,26,28,0.5); line-height: 1.6; max-width: 520px; margin-left: auto; margin-right: auto; margin-bottom: 40px;"
      >
        ByteLabs is a dev house that designs and builds digital products — from concept to launch. We turn your ideas into scalable, polished software.
      </p>

      <!-- CTA -->
      <div data-hero style="opacity:0; display: flex; justify-content: center; margin-bottom: 80px;">
        <a href="#contact" style="display: inline-flex; align-items: center; justify-content: center; padding: 12px 28px; background-color: #181a1c; color: #fff; font-size: 14px; font-weight: 500; border-radius: 50px; text-decoration: none;">
          Start a Project
        </a>
      </div>

      <!-- Product mockup -->
      <div data-hero style="opacity:0; max-width: 1100px; margin-left: auto; margin-right: auto; position: relative;">
        <!-- Gradient blobs -->
        <div class="hero-blob-left"></div>
        <div class="hero-blob-right"></div>

        <!-- Dashboard mockup -->
        <div class="dashboard-mockup">
          <!-- Sidebar - hidden on mobile -->
          <div class="dashboard-sidebar">
            <div class="sidebar-header">
              <div class="sidebar-brand">
                <span>ByteLabs()</span>
                <svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M6 9l6 6 6-6"/></svg>
              </div>
            </div>
            <nav class="sidebar-nav">
              <a href="#" class="nav-item active">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg>
                Dashboard
              </a>
              <a href="#" class="nav-item">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"/></svg>
                Projects
              </a>
              <a href="#" class="nav-item">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
                Team
              </a>
              <a href="#" class="nav-item">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg>
                Settings
              </a>
            </nav>
            <div class="sidebar-footer">
              <div class="user-avatar">SY</div>
              <span class="user-name">Simphiwe Y.</span>
            </div>
          </div>

          <!-- Main content -->
          <div class="dashboard-main">
            <!-- Top header -->
            <div class="dashboard-header">
              <h2>Project Overview</h2>
              <div class="header-actions">
                <button class="action-btn">
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
                </button>
                <button class="action-btn">
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/><path d="M13.73 21a2 2 0 0 1-3.46 0"/></svg>
                </button>
              </div>
            </div>

            <!-- Toolbar -->
            <div class="dashboard-toolbar">
              <div class="toolbar-left">
                <span class="toolbar-label">✦ Active Sprint</span>
                <div class="toggle-wrapper">
                  <div class="toggle-track active">
                    <div class="toggle-thumb"></div>
                  </div>
                </div>
              </div>
              <div class="toolbar-right">
                <button class="toolbar-btn">+ Add Task</button>
                <button class="toolbar-btn primary">
                  <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M22 2L11 13"/><path d="M22 2l-7 20-4-9-9-4 20-7z"/></svg>
                  Deploy
                </button>
              </div>
            </div>

            <!-- Table -->
            <div class="dashboard-table">
              <div class="table-header">
                <div class="th-check"></div>
                <div class="th-project">Project</div>
                <div class="th-status">Status</div>
                <div class="th-progress">Progress</div>
              </div>
              <div class="table-row">
                <div class="td-check"><div class="checkbox"></div></div>
                <div class="td-project">
                  <div class="project-icon-img">
                    <img :src="gaiosophyLogo" alt="Gaiosophy" />
                  </div>
                  <div class="project-info">
                    <span class="project-name">Gaiosophy</span>
                    <span class="project-meta">Seasonal Guide • Web App</span>
                  </div>
                </div>
                <div class="td-status"><span class="status-badge delivered">Delivered</span></div>
                <div class="td-progress"><div class="progress-bar"><div class="progress-fill" style="width:100%"></div></div></div>
              </div>
              <div class="table-row">
                <div class="td-check"><div class="checkbox"></div></div>
                <div class="td-project">
                  <div class="project-icon-img">
                    <img :src="strikepointLogo" alt="StrikePoint" />
                  </div>
                  <div class="project-info">
                    <span class="project-name">StrikePoint</span>
                    <span class="project-meta">Security Platform • Mobile</span>
                  </div>
                </div>
                <div class="td-status"><span class="status-badge delivered">Delivered</span></div>
                <div class="td-progress"><div class="progress-bar"><div class="progress-fill" style="width:100%"></div></div></div>
              </div>
              <div class="table-row">
                <div class="td-check"><div class="checkbox"></div></div>
                <div class="td-project">
                  <div class="project-icon-img">
                    <img :src="happayLogo" alt="Happay" />
                  </div>
                  <div class="project-info">
                    <span class="project-name">Happay</span>
                    <span class="project-meta">Retail Checkout • Mobile</span>
                  </div>
                </div>
                <div class="td-status"><span class="status-badge in-progress">In Progress</span></div>
                <div class="td-progress"><div class="progress-bar"><div class="progress-fill" style="width:65%"></div></div></div>
              </div>
              <div class="table-row">
                <div class="td-check"><div class="checkbox"></div></div>
                <div class="td-project">
                  <div class="project-icon safedeal">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                      <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      <path d="M9 12l2 2 4-4" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                  </div>
                  <div class="project-info">
                    <span class="project-name">SafeDeal</span>
                    <span class="project-meta">P2P Escrow • Mobile</span>
                  </div>
                </div>
                <div class="td-status"><span class="status-badge in-progress">In Progress</span></div>
                <div class="td-progress"><div class="progress-bar"><div class="progress-fill" style="width:25%"></div></div></div>
              </div>
            </div>

            <!-- Footer -->
            <div class="dashboard-footer">
              <span>4 projects</span>
              <span class="footer-divider">•</span>
              <span>2 delivered</span>
              <span class="footer-divider">•</span>
              <span>2 in-house products</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Trusted by section -->
      <div data-hero style="opacity:0; padding-top: 80px; padding-bottom: 60px;">
        <div class="trust-badge">
          <span>Trusted by growing startups</span>
        </div>
        
        <!-- Client logos -->
        <div class="client-logos">
          <div class="logo-item">
            <span style="font-weight: 600; font-size: 18px; letter-spacing: 0.05em; color: #1a1a1a;">GAIOSOPHY</span>
          </div>
          <div class="logo-item">
            <span style="font-weight: 700; font-size: 16px; letter-spacing: 0.1em; color: #1a1a1a;">STRIKEPOINT</span>
          </div>
          <div class="logo-item">
            <div style="display: flex; align-items: center; gap: 6px;">
              <div style="width: 24px; height: 24px; background: #8b5cf6; border-radius: 6px; display: flex; align-items: center; justify-content: center; color: #fff; font-size: 12px; font-weight: 700;">H</div>
              <span style="font-weight: 600; font-size: 16px; color: #1a1a1a;">Happay</span>
            </div>
          </div>
          <div class="logo-item">
            <span style="font-weight: 500; font-size: 17px; color: #1a1a1a; border: 1px solid #1a1a1a; padding: 4px 12px;">ACME</span>
          </div>
        </div>
      </div>

      <!-- Testimonials -->
      <div data-hero style="opacity:0; padding-bottom: 40px;">
        <div class="testimonials-grid">
          <div class="testimonial-card">
            <p class="testimonial-text">
              "ByteLabs delivered our MVP in record time. Their team understood our vision and translated it into a polished product that our users love."
            </p>
            <div class="testimonial-author">
              <div class="author-avatar">SP</div>
              <div class="author-info">
                <span class="author-name">Sophie Spiro</span>
                <span class="author-title">CEO, Gaiosophy</span>
              </div>
            </div>
          </div>
          <div class="testimonial-card">
            <p class="testimonial-text">
              "Working with ByteLabs was seamless. They took our complex requirements and built a mobile app that exceeded expectations."
            </p>
            <div class="testimonial-author">
              <div class="author-avatar">JL</div>
              <div class="author-info">
                <span class="author-name">Jean Le Roux</span>
                <span class="author-title">Founder, StrikePoint</span>
              </div>
            </div>
          </div>
          <div class="testimonial-card">
            <p class="testimonial-text">
              "The attention to detail and technical expertise of ByteLabs is unmatched. They're not just developers, they're true partners."
            </p>
            <div class="testimonial-author">
              <div class="author-avatar">MK</div>
              <div class="author-info">
                <span class="author-name">Mike Kim</span>
                <span class="author-title">CTO, TechStart</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-blob-left {
  position: absolute;
  left: -60px;
  top: 40%;
  transform: translateY(-50%);
  width: 250px;
  height: 250px;
  border-radius: 50%;
  background: rgba(96, 165, 250, 0.2);
  filter: blur(100px);
  pointer-events: none;
}
.hero-blob-right {
  position: absolute;
  right: -60px;
  top: 60%;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background: rgba(167, 139, 250, 0.25);
  filter: blur(100px);
  pointer-events: none;
}

.dashboard-mockup {
  position: relative;
  display: flex;
  border-radius: 16px 16px 0 0;
  border: 1px solid rgba(24, 26, 28, 0.08);
  border-bottom: none;
  background: #fff;
  box-shadow: 0 25px 80px -12px rgba(24, 26, 28, 0.12);
  overflow: hidden;
  min-height: 420px;
}

/* Sidebar */
.dashboard-sidebar {
  width: 200px;
  background: #fff;
  border-right: 1px solid #e8e8e8;
  display: flex;
  flex-direction: column;
  flex-shrink: 0;
}

.sidebar-header {
  padding: 16px;
  border-bottom: 1px solid #f0f0f0;
}

.sidebar-brand {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 14px;
  font-weight: 600;
  color: #1a1a1a;
}

.brand-icon {
  width: 24px;
  height: 24px;
  background: #1a1a1a;
  color: #fff;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 11px;
  font-weight: 700;
}

.sidebar-brand svg {
  margin-left: auto;
  opacity: 0.4;
}

.sidebar-nav {
  padding: 12px 8px;
  flex: 1;
}

.nav-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 12px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 500;
  color: #666;
  text-decoration: none;
  margin-bottom: 4px;
}

.nav-item.active {
  background: #f5f5f7;
  color: #1a1a1a;
}

.nav-item svg {
  opacity: 0.6;
}

.sidebar-footer {
  padding: 12px 16px;
  border-top: 1px solid #f0f0f0;
  display: flex;
  align-items: center;
  gap: 10px;
}

.user-avatar {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 10px;
  font-weight: 600;
}

.user-name {
  font-size: 12px;
  font-weight: 500;
  color: #1a1a1a;
}

/* Main content */
.dashboard-main {
  flex: 1;
  display: flex;
  flex-direction: column;
  background: #fafafa;
  min-width: 0;
}

.dashboard-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px 20px;
  background: #fff;
  border-bottom: 1px solid #e8e8e8;
}

.dashboard-header h2 {
  font-size: 15px;
  font-weight: 600;
  color: #1a1a1a;
}

.header-actions {
  display: flex;
  gap: 8px;
}

.action-btn {
  width: 28px;
  height: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  background: none;
  color: #888;
  border-radius: 6px;
  cursor: pointer;
}

.action-btn:hover {
  background: #f0f0f0;
}

/* Toolbar */
.dashboard-toolbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  background: #fff;
  border-bottom: 1px solid #e8e8e8;
  gap: 12px;
  flex-wrap: wrap;
}

.toolbar-left {
  display: flex;
  align-items: center;
  gap: 10px;
}

.toolbar-label {
  font-size: 13px;
  font-weight: 500;
  color: #555;
}

.toggle-wrapper {
  display: flex;
  align-items: center;
}

.toggle-track {
  width: 36px;
  height: 20px;
  background: #ddd;
  border-radius: 10px;
  position: relative;
  cursor: pointer;
}

.toggle-track.active {
  background: #4a90d9;
}

.toggle-thumb {
  position: absolute;
  width: 16px;
  height: 16px;
  background: #fff;
  border-radius: 50%;
  top: 2px;
  left: 2px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.2);
  transition: left 0.2s;
}

.toggle-track.active .toggle-thumb {
  left: 18px;
}

.toolbar-right {
  display: flex;
  align-items: center;
  gap: 8px;
}

.toolbar-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 6px 14px;
  border: 1px solid #ddd;
  border-radius: 6px;
  background: #fff;
  font-size: 12px;
  font-weight: 500;
  color: #1a1a1a;
  cursor: pointer;
}

.toolbar-btn:hover {
  background: #f5f5f5;
}

.toolbar-btn.primary {
  background: #4a6cf7;
  color: #fff;
  border: none;
}

.toolbar-btn.primary:hover {
  background: #3a5ce5;
}

/* Table */
.dashboard-table {
  flex: 1;
  background: #fff;
  overflow: hidden;
}

.table-header {
  display: grid;
  grid-template-columns: 32px 1fr 100px 120px;
  padding: 10px 16px;
  background: #fafafa;
  border-bottom: 1px solid #e8e8e8;
  font-size: 11px;
  font-weight: 500;
  color: #888;
  text-transform: uppercase;
  letter-spacing: 0.02em;
}

.table-row {
  display: grid;
  grid-template-columns: 32px 1fr 100px 120px;
  padding: 12px 16px;
  border-bottom: 1px solid #f0f0f0;
  align-items: center;
}

.table-row:hover {
  background: #fafafa;
}

.checkbox {
  width: 16px;
  height: 16px;
  border: 2px solid #d0d0d0;
  border-radius: 4px;
}

.td-project {
  display: flex;
  align-items: center;
  gap: 10px;
  min-width: 0;
}

.project-icon {
  width: 28px;
  height: 28px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  font-weight: 700;
  color: #fff;
  flex-shrink: 0;
}

.project-icon.green { background: #10b981; }
.project-icon.blue { background: #3b82f6; }
.project-icon.purple { background: #8b5cf6; }
.project-icon.orange { background: #f59e0b; }
.project-icon.api-gateway { background: #f59e0b; }
.project-icon.safedeal { background: linear-gradient(135deg, #10b981 0%, #059669 100%); }

.project-icon-img {
  width: 28px;
  height: 28px;
  border-radius: 6px;
  overflow: hidden;
  flex-shrink: 0;
}

.project-icon-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.project-info {
  display: flex;
  flex-direction: column;
  min-width: 0;
}

.project-name {
  font-size: 13px;
  font-weight: 600;
  color: #1a1a1a;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.project-meta {
  font-size: 11px;
  color: #999;
}

.status-badge {
  display: inline-block;
  padding: 4px 10px;
  border-radius: 12px;
  font-size: 11px;
  font-weight: 500;
}

.status-badge.delivered {
  background: #d1fae5;
  color: #059669;
}

.status-badge.in-progress {
  background: #e0e7ff;
  color: #4f46e5;
}

.td-progress {
  padding-right: 8px;
}

.progress-bar {
  height: 6px;
  background: #e5e7eb;
  border-radius: 3px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: #10b981;
  border-radius: 3px;
}

/* Footer */
.dashboard-footer {
  display: flex;
  align-items: center;
  padding: 10px 16px;
  background: #fafafa;
  border-top: 1px solid #e8e8e8;
  font-size: 12px;
  color: #888;
  gap: 8px;
}

.footer-divider {
  color: #ccc;
}

/* Trust badge & Logos */
.trust-badge {
  display: flex;
  justify-content: center;
  margin-bottom: 40px;
}

.trust-badge span {
  display: inline-block;
  padding: 8px 20px;
  border-radius: 50px;
  border: 1px solid rgba(24, 26, 28, 0.1);
  font-size: 13px;
  font-weight: 500;
  color: rgba(24, 26, 28, 0.6);
}

.client-logos {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 48px;
  flex-wrap: wrap;
}

.logo-item {
  opacity: 0.7;
  transition: opacity 0.2s;
}

.logo-item:hover {
  opacity: 1;
}

/* Testimonials */
.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.testimonial-card {
  background: #fff;
  border-radius: 16px;
  padding: 24px;
  border: 1px solid rgba(24, 26, 28, 0.06);
  box-shadow: 0 2px 8px rgba(24, 26, 28, 0.04);
}

.testimonial-text {
  font-size: 14px;
  line-height: 1.6;
  color: #333;
  margin-bottom: 20px;
}

.testimonial-author {
  display: flex;
  align-items: center;
  gap: 12px;
}

.author-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 12px;
  font-weight: 600;
}

.author-info {
  display: flex;
  flex-direction: column;
}

.author-name {
  font-size: 13px;
  font-weight: 600;
  color: #1a1a1a;
}

.author-title {
  font-size: 12px;
  color: #888;
}

/* Mobile responsive */
@media (max-width: 768px) {
  .dashboard-mockup {
    min-height: 320px;
  }
  
  .dashboard-sidebar {
    display: none;
  }
  
  .table-header,
  .table-row {
    grid-template-columns: 28px 1fr 80px;
  }
  
  .th-progress,
  .td-progress {
    display: none;
  }
  
  .dashboard-toolbar {
    padding: 8px 12px;
  }
  
  .toolbar-left {
    display: none;
  }
  
  .dashboard-header {
    padding: 12px 16px;
  }
  
  .dashboard-header h2 {
    font-size: 14px;
  }
  
  .table-header {
    padding: 8px 12px;
    font-size: 10px;
  }
  
  .table-row {
    padding: 10px 12px;
  }
  
  .project-icon {
    width: 24px;
    height: 24px;
    font-size: 10px;
  }
  
  .project-icon-img {
    width: 24px;
    height: 24px;
  }
  
  .project-name {
    font-size: 12px;
  }
  
  .project-meta {
    font-size: 10px;
  }
  
  .status-badge {
    padding: 3px 8px;
    font-size: 10px;
  }
  
  .dashboard-footer {
    padding: 8px 12px;
    font-size: 11px;
  }
  
  .client-logos {
    gap: 24px;
  }
  
  .testimonials-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
  
  .testimonial-card {
    padding: 20px;
  }
}

@media (max-width: 480px) {
  .dashboard-mockup {
    min-height: 280px;
  }
  
  .toolbar-btn {
    padding: 5px 10px;
    font-size: 11px;
  }
  
  .header-actions {
    display: none;
  }
  
  .client-logos {
    gap: 16px;
  }
  
  .logo-item span {
    font-size: 14px !important;
  }
}
</style>
