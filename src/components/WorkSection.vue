<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const headerRef = ref(null)
const showcaseRef = ref(null)
const stops = []

onMounted(() => {
  if (headerRef.value) {
    stops.push(
      inView(headerRef.value, ({ target }) => {
        animate(target, { opacity: [0, 1], y: [32, 0] }, { duration: 0.8, easing: [0.25, 0.1, 0.25, 1] })
      }, { amount: 0.2 })
    )
  }
  if (showcaseRef.value) {
    const items = showcaseRef.value.querySelectorAll('[data-project]')
    stops.push(
      inView(showcaseRef.value, () => {
        animate(
          items,
          { opacity: [0, 1], y: [40, 0] },
          { duration: 0.7, delay: stagger(0.15, { start: 0.1 }), easing: [0.25, 0.1, 0.25, 1] }
        )
      }, { amount: 0.05 })
    )
  }
})

onUnmounted(() => stops.forEach((s) => s()))
</script>

<template>
  <section id="work" class="work-section">
    <div class="work-inner">

      <!-- Header -->
      <div ref="headerRef" style="opacity:0" class="work-header">
        <span class="work-label">Selected Work</span>
        <h2 class="work-title">Case studies</h2>
      </div>

      <div ref="showcaseRef" class="showcase">

        <!-- ═══ CreditFlow — Hero Card ═══ -->
        <div data-project style="opacity:0" class="case case-hero">
          <div class="case-content">
            <div class="case-meta">
              <span class="case-tag tag-delivered">Delivered</span>
              <span class="case-stack">Vue.js · Django · PostgreSQL</span>
            </div>
            <h3 class="case-name case-name-lg">CreditFlow</h3>
            <p class="case-desc">
              White-label lending platform that automates the entire short-term loan journey — from identity verification and credit checks to affordability assessment, DebiCheck mandates, and instant disbursement. Fully digital, zero documents.
            </p>
          </div>
          <div class="case-visual visual-credit">
            <!-- Dashboard mockup -->
            <div class="mock-dashboard">
              <div class="mock-topbar">
                <div class="mock-dots">
                  <span></span><span></span><span></span>
                </div>
                <span class="mock-url">app.creditflow.co.za</span>
              </div>
              <div class="mock-body">
                <div class="mock-sidebar">
                  <div class="sb-item active"></div>
                  <div class="sb-item"></div>
                  <div class="sb-item"></div>
                  <div class="sb-item"></div>
                </div>
                <div class="mock-main">
                  <div class="mock-stat-row">
                    <div class="mock-stat">
                      <span class="ms-val">R2.4M</span>
                      <span class="ms-label">Disbursed</span>
                    </div>
                    <div class="mock-stat">
                      <span class="ms-val">342</span>
                      <span class="ms-label">Applications</span>
                    </div>
                    <div class="mock-stat">
                      <span class="ms-val">4.2m</span>
                      <span class="ms-label">Avg. Time</span>
                    </div>
                  </div>
                  <div class="mock-pipeline">
                    <div class="pipe-step done">ID Verify</div>
                    <div class="pipe-line done"></div>
                    <div class="pipe-step done">Credit</div>
                    <div class="pipe-line done"></div>
                    <div class="pipe-step done">Afford.</div>
                    <div class="pipe-line active"></div>
                    <div class="pipe-step active">Payout</div>
                  </div>
                  <div class="mock-table">
                    <div class="mt-row"><span class="mt-name">N. Dlamini</span><span class="mt-amt">R8,500</span><span class="mt-badge green">Approved</span></div>
                    <div class="mt-row"><span class="mt-name">T. Molefe</span><span class="mt-amt">R12,000</span><span class="mt-badge blue">Processing</span></div>
                    <div class="mt-row"><span class="mt-name">S. Naidoo</span><span class="mt-amt">R5,200</span><span class="mt-badge green">Disbursed</span></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- ═══ Two-up: Gaiosophy & StrikePoint ═══ -->
        <div class="case-pair">

          <!-- Gaiosophy -->
          <div data-project style="opacity:0" class="case case-half">
            <div class="case-meta">
              <span class="case-tag tag-delivered">Delivered</span>
              <span class="case-stack">Flutter · Dart · Firebase</span>
            </div>
            <h3 class="case-name">Gaiosophy</h3>
            <p class="case-desc">
              A seasonal guide rooted in the Celtic Wheel of the Year — folklore, foraging recipes, sacred crafts, earth-based rituals, and wisdom teachings of the British Isles.
            </p>
            <div class="case-visual visual-gaio">
              <div class="mock-phone">
                <div class="phone-notch"></div>
                <div class="phone-screen">
                  <div class="gaio-wheel">
                    <div class="wheel-ring">
                      <span class="w-season w-spring">Imbolc</span>
                      <span class="w-season w-summer">Beltane</span>
                      <span class="w-season w-autumn">Lughnasa</span>
                      <span class="w-season w-winter">Samhain</span>
                    </div>
                    <div class="wheel-center">
                      <span>Celtic</span>
                      <span>Wheel</span>
                    </div>
                  </div>
                  <div class="gaio-cards">
                    <div class="gc">Foraging</div>
                    <div class="gc">Rituals</div>
                    <div class="gc">Crafts</div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- StrikePoint -->
          <div data-project style="opacity:0" class="case case-half case-dark-accent">
            <div class="case-meta">
              <span class="case-tag tag-delivered">Delivered</span>
              <span class="case-stack">Flutter · Dart · Firebase</span>
            </div>
            <h3 class="case-name">StrikePoint</h3>
            <p class="case-desc">
              A marketplace for executive protection — like Upwork for CPO, bodyguard, and security freelancers. Built for a Boksburg-based tactical operations startup.
            </p>
            <div class="case-visual visual-strike">
              <div class="mock-phone phone-dark">
                <div class="phone-notch"></div>
                <div class="phone-screen">
                  <div class="strike-header">Active Jobs</div>
                  <div class="strike-job">
                    <div class="sj-avatar">JM</div>
                    <div class="sj-info">
                      <span class="sj-title">Close Protection</span>
                      <span class="sj-loc">Sandton · 3 days</span>
                    </div>
                    <span class="sj-status active">Live</span>
                  </div>
                  <div class="strike-job">
                    <div class="sj-avatar">KN</div>
                    <div class="sj-info">
                      <span class="sj-title">Event Security</span>
                      <span class="sj-loc">Boksburg · 1 day</span>
                    </div>
                    <span class="sj-status pending">New</span>
                  </div>
                  <div class="strike-job">
                    <div class="sj-avatar">TS</div>
                    <div class="sj-info">
                      <span class="sj-title">VIP Escort</span>
                      <span class="sj-loc">Pretoria · 5 days</span>
                    </div>
                    <span class="sj-status active">Live</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- ═══ Two-up: Happay & SafeDeal ═══ -->
        <div class="case-pair">

          <!-- Happay -->
          <div data-project style="opacity:0" class="case case-half case-violet">
            <div class="case-meta">
              <span class="case-tag tag-inhouse">In-house</span>
              <span class="case-stack">Flutter · Dart · Firestore</span>
            </div>
            <h3 class="case-name">Happay</h3>
            <p class="case-desc">
              Our own fintech product — a modern retail checkout and payment platform built to simplify commerce for small businesses across South Africa.
            </p>
            <div class="case-visual visual-happay">
              <div class="mock-phone phone-violet">
                <div class="phone-notch"></div>
                <div class="phone-screen">
                  <div class="happay-balance">
                    <span class="hb-label">Balance</span>
                    <span class="hb-amount">R12,840</span>
                  </div>
                  <div class="happay-actions">
                    <div class="ha-btn">Send</div>
                    <div class="ha-btn">Request</div>
                    <div class="ha-btn">Scan</div>
                  </div>
                  <div class="happay-tx">
                    <div class="htx"><span class="htx-name">Pick n Pay</span><span class="htx-amt red">-R350</span></div>
                    <div class="htx"><span class="htx-name">Client payment</span><span class="htx-amt green">+R1,200</span></div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- SafeDeal -->
          <div data-project style="opacity:0" class="case case-half case-teal">
            <div class="case-meta">
              <span class="case-tag tag-inhouse">In-house</span>
              <span class="case-stack">Flutter · Dart · Firestore</span>
            </div>
            <h3 class="case-name">SafeDeal</h3>
            <p class="case-desc">
              Peer-to-peer escrow for safe online transactions. Holds funds until both buyer and seller confirm — eliminating fraud in private sales.
            </p>
            <div class="case-visual visual-safedeal">
              <div class="escrow-flow">
                <div class="ef-node buyer">
                  <div class="ef-icon">B</div>
                  <span>Buyer pays</span>
                </div>
                <div class="ef-arrow">
                  <svg viewBox="0 0 40 12" fill="none"><path d="M0 6h36m0 0l-4-4m4 4l-4 4" stroke="currentColor" stroke-width="1.5"/></svg>
                </div>
                <div class="ef-node escrow">
                  <div class="ef-icon">
                    <svg viewBox="0 0 16 16" fill="none" width="14" height="14"><path d="M8 1L1 5v6l7 4 7-4V5L8 1z" stroke="currentColor" stroke-width="1.2"/><path d="M8 7v4" stroke="currentColor" stroke-width="1.2"/><circle cx="8" cy="5.5" r="1" fill="currentColor"/></svg>
                  </div>
                  <span>Held in escrow</span>
                </div>
                <div class="ef-arrow">
                  <svg viewBox="0 0 40 12" fill="none"><path d="M0 6h36m0 0l-4-4m4 4l-4 4" stroke="currentColor" stroke-width="1.5"/></svg>
                </div>
                <div class="ef-node seller">
                  <div class="ef-icon">S</div>
                  <span>Seller receives</span>
                </div>
              </div>
              <div class="escrow-status">
                <div class="es-bar"><div class="es-fill"></div></div>
                <span class="es-text">Funds secured · waiting for confirmation</span>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
/* ─── Section ─── */
.work-section {
  background: var(--color-light-bg);
  padding: 100px 24px 120px;
}

.work-inner {
  max-width: 1112px;
  margin: 0 auto;
}

/* ─── Header ─── */
.work-header {
  margin-bottom: 64px;
}

.work-label {
  display: block;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: rgba(24, 26, 28, 0.35);
  margin-bottom: 12px;
}

.work-title {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.5rem, 6vw, 4.5rem);
  font-weight: 400;
  color: var(--color-dark);
  letter-spacing: -0.03em;
  line-height: 1;
}

/* ─── Showcase ─── */
.showcase {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* ─── Case card base ─── */
.case {
  border-radius: 20px;
  overflow: hidden;
  position: relative;
}

/* ─── Hero card (CreditFlow) ─── */
.case-hero {
  background: var(--color-dark);
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  min-height: 480px;
}

.case-hero .case-content {
  padding: 48px 40px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.case-hero .case-name-lg {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2rem, 4vw, 3.2rem);
  color: #fff;
  letter-spacing: -0.02em;
  line-height: 1.1;
  margin-bottom: 16px;
}

.case-hero .case-desc {
  font-size: 14px;
  line-height: 1.7;
  color: rgba(255, 255, 255, 0.5);
  max-width: 420px;
}

.case-hero .case-meta {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
}

.case-hero .case-stack {
  font-size: 11px;
  color: rgba(255, 255, 255, 0.3);
}

/* ─── Half cards ─── */
.case-pair {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.case-half {
  background: #fff;
  padding: 36px 32px 0;
  display: flex;
  flex-direction: column;
}

.case-half .case-meta {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 16px;
}

.case-half .case-name {
  font-size: 22px;
  font-weight: 700;
  color: var(--color-dark);
  letter-spacing: -0.02em;
  margin-bottom: 8px;
}

.case-half .case-desc {
  font-size: 13px;
  line-height: 1.65;
  color: rgba(24, 26, 28, 0.5);
  margin-bottom: 28px;
}

.case-half .case-stack {
  font-size: 11px;
  color: rgba(24, 26, 28, 0.3);
}

/* Dark accent variant */
.case-dark-accent {
  background: #1a1c1e;
}

.case-dark-accent .case-name {
  color: #fff;
}

.case-dark-accent .case-desc {
  color: rgba(255, 255, 255, 0.45);
}

.case-dark-accent .case-stack {
  color: rgba(255, 255, 255, 0.25);
}

/* Violet variant */
.case-violet {
  background: linear-gradient(135deg, #f5f3ff 0%, #ede9fe 100%);
}

/* Teal variant */
.case-teal {
  background: linear-gradient(135deg, #f0fdfa 0%, #ccfbf1 100%);
}

/* ─── Tags ─── */
.case-tag {
  font-size: 10px;
  font-weight: 600;
  padding: 4px 12px;
  border-radius: 99px;
  letter-spacing: 0.02em;
}

.tag-delivered {
  background: rgba(16, 185, 129, 0.12);
  color: #059669;
}

.tag-inhouse {
  background: rgba(139, 92, 246, 0.12);
  color: #7c3aed;
}

.case-hero .tag-delivered {
  background: rgba(16, 185, 129, 0.15);
  color: #34d399;
}

/* ─── Visuals ─── */
.case-visual {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  padding-top: 20px;
  overflow: hidden;
}

.visual-credit {
  background: linear-gradient(180deg, transparent 0%, rgba(59, 130, 246, 0.08) 100%);
  padding: 24px 24px 0;
}

/* ─── Dashboard mockup ─── */
.mock-dashboard {
  width: 100%;
  max-width: 480px;
  background: #111318;
  border-radius: 12px 12px 0 0;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-bottom: none;
}

.mock-topbar {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 16px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}

.mock-dots {
  display: flex;
  gap: 5px;
}

.mock-dots span {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.12);
}

.mock-dots span:first-child { background: #ef4444; }
.mock-dots span:nth-child(2) { background: #eab308; }
.mock-dots span:last-child { background: #22c55e; }

.mock-url {
  font-size: 10px;
  color: rgba(255, 255, 255, 0.25);
  background: rgba(255, 255, 255, 0.05);
  padding: 3px 10px;
  border-radius: 6px;
}

.mock-body {
  display: flex;
  min-height: 260px;
}

.mock-sidebar {
  width: 44px;
  background: rgba(255, 255, 255, 0.02);
  border-right: 1px solid rgba(255, 255, 255, 0.05);
  padding: 12px 8px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.sb-item {
  height: 28px;
  border-radius: 6px;
  background: rgba(255, 255, 255, 0.04);
}

.sb-item.active {
  background: rgba(59, 130, 246, 0.3);
}

.mock-main {
  flex: 1;
  padding: 16px;
}

.mock-stat-row {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}

.mock-stat {
  flex: 1;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 8px;
  padding: 10px 8px;
  text-align: center;
}

.ms-val {
  display: block;
  font-size: 13px;
  font-weight: 700;
  color: #fff;
  letter-spacing: -0.02em;
}

.ms-label {
  display: block;
  font-size: 8px;
  color: rgba(255, 255, 255, 0.3);
  margin-top: 2px;
}

.mock-pipeline {
  display: flex;
  align-items: center;
  gap: 0;
  margin-bottom: 16px;
  padding: 0 4px;
}

.pipe-step {
  font-size: 8px;
  font-weight: 600;
  padding: 4px 6px;
  border-radius: 4px;
  white-space: nowrap;
}

.pipe-step.done {
  color: #34d399;
  background: rgba(16, 185, 129, 0.12);
}

.pipe-step.active {
  color: #60a5fa;
  background: rgba(59, 130, 246, 0.15);
}

.pipe-line {
  flex: 1;
  height: 1px;
  min-width: 8px;
}

.pipe-line.done { background: rgba(16, 185, 129, 0.3); }
.pipe-line.active { background: rgba(59, 130, 246, 0.2); }

.mock-table {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.mt-row {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 6px 8px;
  background: rgba(255, 255, 255, 0.03);
  border-radius: 6px;
}

.mt-name {
  flex: 1;
  font-size: 9px;
  color: rgba(255, 255, 255, 0.5);
}

.mt-amt {
  font-size: 9px;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.7);
}

.mt-badge {
  font-size: 7px;
  font-weight: 600;
  padding: 2px 6px;
  border-radius: 99px;
}

.mt-badge.green {
  color: #34d399;
  background: rgba(16, 185, 129, 0.12);
}

.mt-badge.blue {
  color: #60a5fa;
  background: rgba(59, 130, 246, 0.12);
}

/* ─── Phone mockup ─── */
.mock-phone {
  width: 220px;
  background: #fff;
  border-radius: 28px 28px 0 0;
  border: 1px solid rgba(0, 0, 0, 0.08);
  border-bottom: none;
  position: relative;
  overflow: hidden;
  box-shadow: 0 -8px 40px rgba(0, 0, 0, 0.08);
}

.phone-dark {
  background: #0f1115;
  border-color: rgba(255, 255, 255, 0.08);
  box-shadow: 0 -8px 40px rgba(0, 0, 0, 0.3);
}

.phone-violet {
  background: #faf5ff;
  border-color: rgba(139, 92, 246, 0.15);
  box-shadow: 0 -8px 40px rgba(139, 92, 246, 0.1);
}

.phone-notch {
  width: 80px;
  height: 20px;
  background: inherit;
  border-radius: 0 0 16px 16px;
  margin: 0 auto;
  position: relative;
}

.phone-notch::before {
  content: '';
  position: absolute;
  top: 6px;
  left: 50%;
  transform: translateX(-50%);
  width: 40px;
  height: 4px;
  border-radius: 99px;
  background: rgba(0, 0, 0, 0.15);
}

.phone-dark .phone-notch::before {
  background: rgba(255, 255, 255, 0.15);
}

.phone-screen {
  padding: 8px 16px 0;
}

/* ─── Gaiosophy wheel ─── */
.gaio-wheel {
  position: relative;
  width: 140px;
  height: 140px;
  margin: 0 auto 12px;
}

.wheel-ring {
  position: absolute;
  inset: 0;
  border-radius: 50%;
  border: 1.5px solid rgba(217, 119, 6, 0.2);
}

.w-season {
  position: absolute;
  font-size: 8px;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 99px;
}

.w-spring { top: -4px; left: 50%; transform: translateX(-50%); color: #059669; background: #ecfdf5; }
.w-summer { right: -8px; top: 50%; transform: translateY(-50%); color: #d97706; background: #fffbeb; }
.w-autumn { bottom: -4px; left: 50%; transform: translateX(-50%); color: #ea580c; background: #fff7ed; }
.w-winter { left: -8px; top: 50%; transform: translateY(-50%); color: #2563eb; background: #eff6ff; }

.wheel-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  font-size: 9px;
  font-weight: 600;
  color: rgba(0, 0, 0, 0.25);
  line-height: 1.3;
}

.gaio-cards {
  display: flex;
  gap: 6px;
  padding-bottom: 4px;
}

.gc {
  flex: 1;
  text-align: center;
  font-size: 8px;
  font-weight: 600;
  color: #92400e;
  background: rgba(217, 119, 6, 0.08);
  padding: 8px 0;
  border-radius: 8px;
}

/* ─── StrikePoint ─── */
.strike-header {
  font-size: 11px;
  font-weight: 700;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 10px;
}

.strike-job {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px;
  background: rgba(255, 255, 255, 0.04);
  border-radius: 10px;
  margin-bottom: 6px;
}

.sj-avatar {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.08);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 8px;
  font-weight: 700;
  color: rgba(255, 255, 255, 0.5);
  flex-shrink: 0;
}

.sj-info { flex: 1; min-width: 0; }

.sj-title {
  display: block;
  font-size: 10px;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.8);
}

.sj-loc {
  display: block;
  font-size: 8px;
  color: rgba(255, 255, 255, 0.25);
}

.sj-status {
  font-size: 8px;
  font-weight: 600;
  padding: 2px 8px;
  border-radius: 99px;
}

.sj-status.active {
  color: #34d399;
  background: rgba(16, 185, 129, 0.15);
}

.sj-status.pending {
  color: #fbbf24;
  background: rgba(234, 179, 8, 0.15);
}

/* ─── Happay ─── */
.happay-balance {
  text-align: center;
  margin-bottom: 14px;
}

.hb-label {
  display: block;
  font-size: 9px;
  color: rgba(139, 92, 246, 0.5);
  margin-bottom: 2px;
}

.hb-amount {
  display: block;
  font-size: 26px;
  font-weight: 700;
  color: #7c3aed;
  letter-spacing: -0.03em;
}

.happay-actions {
  display: flex;
  gap: 6px;
  margin-bottom: 14px;
}

.ha-btn {
  flex: 1;
  text-align: center;
  font-size: 9px;
  font-weight: 600;
  color: #7c3aed;
  background: rgba(139, 92, 246, 0.1);
  padding: 8px 0;
  border-radius: 10px;
}

.happay-tx {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.htx {
  display: flex;
  justify-content: space-between;
  padding: 6px 8px;
  background: rgba(139, 92, 246, 0.04);
  border-radius: 8px;
}

.htx-name {
  font-size: 9px;
  color: rgba(0, 0, 0, 0.5);
}

.htx-amt {
  font-size: 9px;
  font-weight: 700;
}

.htx-amt.red { color: #ef4444; }
.htx-amt.green { color: #059669; }

/* ─── SafeDeal ─── */
.visual-safedeal {
  padding: 24px 16px 28px;
  align-items: center;
  flex-direction: column;
}

.escrow-flow {
  display: flex;
  align-items: center;
  gap: 0;
  width: 100%;
  max-width: 320px;
}

.ef-node {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
}

.ef-node span {
  font-size: 9px;
  font-weight: 500;
  color: rgba(0, 0, 0, 0.4);
  white-space: nowrap;
}

.ef-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  font-weight: 700;
}

.buyer .ef-icon {
  background: rgba(6, 182, 212, 0.12);
  color: #0891b2;
}

.escrow .ef-icon {
  background: rgba(16, 185, 129, 0.12);
  color: #059669;
}

.seller .ef-icon {
  background: rgba(217, 119, 6, 0.12);
  color: #d97706;
}

.ef-arrow {
  flex: 1;
  min-width: 20px;
  padding: 0 4px;
  color: rgba(0, 0, 0, 0.15);
}

.ef-arrow svg {
  width: 100%;
  height: 12px;
}

.escrow-status {
  margin-top: 16px;
  text-align: center;
  width: 100%;
  max-width: 320px;
}

.es-bar {
  height: 3px;
  background: rgba(16, 185, 129, 0.12);
  border-radius: 99px;
  overflow: hidden;
  margin-bottom: 8px;
}

.es-fill {
  width: 65%;
  height: 100%;
  background: #10b981;
  border-radius: 99px;
}

.es-text {
  font-size: 9px;
  color: rgba(0, 0, 0, 0.3);
}

/* ─── Responsive ─── */
@media (max-width: 768px) {
  .work-section {
    padding: 80px 16px 96px;
  }

  .case-hero {
    grid-template-columns: 1fr;
    min-height: auto;
  }

  .case-hero .case-content {
    padding: 32px 24px 0;
  }

  .visual-credit {
    padding: 20px 16px 0;
  }

  .case-pair {
    grid-template-columns: 1fr;
  }

  .case-half {
    padding: 28px 24px 0;
  }

  .mock-phone {
    width: 200px;
  }
}
</style>
