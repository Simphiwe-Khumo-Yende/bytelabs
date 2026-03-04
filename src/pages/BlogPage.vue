<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const articleRef = ref(null)

onMounted(() => {
  if (!articleRef.value) return
  
  inView(articleRef.value, () => {
    const items = articleRef.value.querySelectorAll('[data-animate]')
    animate(
      items,
      { opacity: [0, 1], y: [30, 0] },
      { duration: 0.7, delay: stagger(0.1), easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.1 })
})
</script>

<template>
  <article ref="articleRef" class="blog-page">
    <!-- Hero -->
    <header data-animate class="blog-hero">
      <div class="hero-content">
        <div class="blog-meta">
          <span class="blog-category">Product</span>
          <span class="blog-date">March 2026</span>
        </div>
        <h1 class="blog-title">The Future of Frictionless Commerce: Introducing Happay and SafeDeal</h1>
        <p class="blog-subtitle">Digital commerce is evolving rapidly. Consumers expect speed, convenience, and security when making purchases. Two emerging platforms designed to solve these problems are Happay and SafeDeal.</p>
        
        <div class="author-section">
          <div class="author-avatar">SY</div>
          <div class="author-info">
            <span class="author-name">Simphiwe Yende</span>
            <span class="author-role">Founder, Happay Pty Ltd & SafeDeal</span>
          </div>
        </div>
      </div>
    </header>

    <!-- Content -->
    <div class="blog-content-wrapper">
      <div class="blog-content">
        <!-- Intro -->
        <section data-animate class="content-section intro-section">
          <p class="lead-text">Each tackles a different but critical friction in modern commerce: <strong>long retail queues</strong> and <strong>unsafe peer-to-peer transactions</strong>.</p>
        </section>

        <!-- Happay Section -->
        <section data-animate class="content-section">
          <div class="section-badge happay-badge">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M6 2L3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"/>
              <line x1="3" y1="6" x2="21" y2="6"/>
              <path d="M16 10a4 4 0 0 1-8 0"/>
            </svg>
            Happay
          </div>
          <h2>The Queue-Free Retail Checkout Experience</h2>
          
          <div class="image-grid">
            <img src="https://www.lsretail.com/hs-fs/hubfs/BLOG_IN_person_shopping_scan_pay_go.jpg?height=400&name=BLOG_IN_person_shopping_scan_pay_go.jpg&width=600" alt="Scan and pay shopping experience" class="featured-image" />
          </div>

          <h3>What is Happay?</h3>
          <p><strong>Happay</strong> is a <strong>queue-free retail checkout application</strong> that allows shoppers to scan products with their phones while shopping and pay instantly without waiting in line.</p>
          <p>Instead of standing at a traditional checkout counter, customers simply <strong>scan items as they place them in their basket</strong>, complete payment through the app, and walk out of the store.</p>

          <h3>How Happay Works</h3>
          <p>The experience is designed to be simple and fast:</p>
          
          <div class="steps-list">
            <div class="step-item">
              <div class="step-number">1</div>
              <div class="step-content">
                <h4>Scan while shopping</h4>
                <p>Customers scan each product's barcode using their smartphone.</p>
              </div>
            </div>
            <div class="step-item">
              <div class="step-number">2</div>
              <div class="step-content">
                <h4>Real-time cart tracking</h4>
                <p>The app builds a digital cart with pricing and totals.</p>
              </div>
            </div>
            <div class="step-item">
              <div class="step-number">3</div>
              <div class="step-content">
                <h4>Instant digital payment</h4>
                <p>Users pay through integrated payment methods such as cards, digital wallets, or mobile banking.</p>
              </div>
            </div>
            <div class="step-item">
              <div class="step-number">4</div>
              <div class="step-content">
                <h4>Smart exit verification</h4>
                <p>AI and store monitoring systems verify transactions and reduce the risk of theft.</p>
              </div>
            </div>
          </div>

          <h3>Why Happay Matters</h3>
          <p>Retail stores face two major problems today:</p>
          <ul class="bullet-list">
            <li>Long checkout queues</li>
            <li>High operational costs for cashiers</li>
          </ul>
          <p>Happay solves both by turning every customer's smartphone into a <strong>personal checkout system</strong>.</p>

          <div class="benefits-grid">
            <div class="benefit-card">
              <h4>For shoppers</h4>
              <ul>
                <li>No waiting in line</li>
                <li>Faster shopping experience</li>
                <li>Real-time spending visibility</li>
              </ul>
            </div>
            <div class="benefit-card">
              <h4>For retailers</h4>
              <ul>
                <li>Reduced checkout infrastructure costs</li>
                <li>Higher store throughput</li>
                <li>Data insights on customer behavior</li>
              </ul>
            </div>
          </div>

          <p class="highlight-text">Happay represents the next generation of <strong>"scan-and-go retail"</strong>, helping stores modernize the shopping experience while improving efficiency.</p>
        </section>

        <!-- SafeDeal Section -->
        <section data-animate class="content-section">
          <div class="section-badge safedeal-badge">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
              <path d="M9 12l2 2 4-4"/>
            </svg>
            SafeDeal
          </div>
          <h2>The Trust Layer for Online Marketplace Transactions</h2>

          <div class="image-grid">
            <img src="https://static.wixstatic.com/media/6067b3_40e190c6869e46dd88f26be1ef939c0b~mv2.png/v1/fill/w_1200,h_675,al_c/Building%20Trust%20in%20E-Commerce.png" alt="Building trust in e-commerce" class="featured-image" />
          </div>

          <h3>What is SafeDeal?</h3>
          <p><strong>SafeDeal</strong> is a <strong>secure transaction infrastructure for peer-to-peer online trading</strong>.</p>
          <p>It protects buyers and sellers when trading on platforms like:</p>
          <ul class="bullet-list platform-list">
            <li>Facebook Marketplace</li>
            <li>Instagram sellers</li>
            <li>WhatsApp trading groups</li>
            <li>TikTok sellers</li>
          </ul>
          <p>Instead of sending money directly to strangers, SafeDeal acts as a <strong>trusted intermediary</strong> that manages verification, payment security, and delivery.</p>

          <h3>How SafeDeal Works</h3>
          <p>SafeDeal introduces a structured process for online deals:</p>

          <div class="steps-list safedeal-steps">
            <div class="step-item">
              <div class="step-number">1</div>
              <div class="step-content">
                <h4>Identity Verification</h4>
                <p>Both buyer and seller verify their identities to reduce fraud.</p>
              </div>
            </div>
            <div class="step-item">
              <div class="step-number">2</div>
              <div class="step-content">
                <h4>Secure Payment Escrow</h4>
                <p>The buyer sends money to SafeDeal, not directly to the seller.</p>
              </div>
            </div>
            <div class="step-item">
              <div class="step-number">3</div>
              <div class="step-content">
                <h4>Product Verification</h4>
                <p>Items may be inspected or confirmed before delivery.</p>
              </div>
            </div>
            <div class="step-item">
              <div class="step-number">4</div>
              <div class="step-content">
                <h4>Controlled Delivery</h4>
                <p>A courier collects and delivers the item safely.</p>
              </div>
            </div>
            <div class="step-item">
              <div class="step-number">5</div>
              <div class="step-content">
                <h4>Funds Release</h4>
                <p>Once the buyer confirms everything is correct, SafeDeal releases the payment.</p>
              </div>
            </div>
          </div>

          <h3>The Problem SafeDeal Solves</h3>
          <p>Peer-to-peer trading is growing rapidly, but it comes with major risks:</p>
          <ul class="bullet-list risk-list">
            <li>Online scams</li>
            <li>Fake sellers</li>
            <li>Non-delivery of goods</li>
            <li>Payment fraud</li>
          </ul>
          <p>SafeDeal creates a <strong>trust infrastructure for digital trading</strong>, ensuring that both sides of the transaction are protected.</p>

          <div class="benefits-grid">
            <div class="benefit-card">
              <h4>For buyers</h4>
              <ul>
                <li>Protection against scams</li>
                <li>Secure payments</li>
                <li>Verified sellers</li>
              </ul>
            </div>
            <div class="benefit-card">
              <h4>For sellers</h4>
              <ul>
                <li>Guaranteed payment</li>
                <li>Reduced fraud risk</li>
                <li>Trusted transaction process</li>
              </ul>
            </div>
          </div>

          <p class="highlight-text">SafeDeal essentially functions as <strong>PayPal-style protection combined with escrow and delivery verification</strong>, specifically built for marketplace trading.</p>
        </section>

        <!-- Summary Section -->
        <section data-animate class="content-section summary-section">
          <h2>The Bigger Picture</h2>
          <p>Both Happay and SafeDeal aim to remove friction from commerce:</p>

          <div class="comparison-table">
            <div class="table-header">
              <div class="th">Platform</div>
              <div class="th">Problem Solved</div>
              <div class="th">Core Idea</div>
            </div>
            <div class="table-row">
              <div class="td platform-name happay-name">Happay</div>
              <div class="td">Retail checkout queues</div>
              <div class="td">Scan-and-go shopping</div>
            </div>
            <div class="table-row">
              <div class="td platform-name safedeal-name">SafeDeal</div>
              <div class="td">Unsafe online marketplace transactions</div>
              <div class="td">Escrow + verification infrastructure</div>
            </div>
          </div>

          <p class="conclusion">Together, they represent a future where <strong>transactions are faster, safer, and more efficient</strong>, whether inside physical stores or across digital marketplaces.</p>
        </section>

        <!-- CTA Section -->
        <section data-animate class="content-section cta-section">
          <div class="cta-card">
            <h3>Interested in partnering or investing?</h3>
            <p>We're building the future of commerce in South Africa. Get in touch to learn more about Happay and SafeDeal.</p>
            <a href="/#contact" class="cta-button">Contact ByteLabs</a>
          </div>
        </section>
      </div>
    </div>
  </article>
</template>

<style scoped>
.blog-page {
  background: #fff;
  min-height: 100vh;
}

/* Hero */
.blog-hero {
  background: linear-gradient(180deg, #f5f5f7 0%, #fff 100%);
  padding: 140px 24px 80px;
}

.hero-content {
  max-width: 800px;
  margin: 0 auto;
}

.blog-meta {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 24px;
}

.blog-category {
  font-size: 12px;
  font-weight: 600;
  color: #42b883;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  background: #e8fff0;
  padding: 6px 12px;
  border-radius: 20px;
}

.blog-date {
  font-size: 13px;
  color: #888;
}

.blog-title {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.2rem, 5vw, 3.5rem);
  font-weight: 400;
  color: #1a1a1a;
  letter-spacing: -0.02em;
  line-height: 1.15;
  margin-bottom: 24px;
}

.blog-subtitle {
  font-size: 18px;
  color: #666;
  line-height: 1.7;
  margin-bottom: 40px;
}

.author-section {
  display: flex;
  align-items: center;
  gap: 14px;
  padding-top: 24px;
  border-top: 1px solid #eee;
}

.author-avatar {
  width: 48px;
  height: 48px;
  background: linear-gradient(135deg, #42b883 0%, #35495e 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 14px;
  font-weight: 700;
}

.author-info {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.author-name {
  font-size: 15px;
  font-weight: 700;
  color: #1a1a1a;
}

.author-role {
  font-size: 13px;
  color: #888;
}

/* Content */
.blog-content-wrapper {
  padding: 60px 24px 100px;
}

.blog-content {
  max-width: 720px;
  margin: 0 auto;
}

.content-section {
  margin-bottom: 64px;
}

.intro-section {
  padding-bottom: 48px;
  border-bottom: 1px solid #eee;
}

.lead-text {
  font-size: 20px;
  color: #444;
  line-height: 1.7;
}

/* Section badges */
.section-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 14px;
  font-weight: 600;
  padding: 10px 16px;
  border-radius: 12px;
  margin-bottom: 20px;
}

.happay-badge {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
}

.safedeal-badge {
  background: linear-gradient(135deg, #10b981 0%, #059669 100%);
  color: #fff;
}

h2 {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(1.8rem, 4vw, 2.4rem);
  font-weight: 400;
  color: #1a1a1a;
  letter-spacing: -0.02em;
  margin-bottom: 32px;
}

h3 {
  font-size: 20px;
  font-weight: 700;
  color: #1a1a1a;
  margin-top: 40px;
  margin-bottom: 16px;
}

p {
  font-size: 16px;
  color: #555;
  line-height: 1.8;
  margin-bottom: 16px;
}

strong {
  color: #1a1a1a;
  font-weight: 600;
}

/* Images */
.image-grid {
  margin: 32px 0;
  border-radius: 16px;
  overflow: hidden;
}

.featured-image {
  width: 100%;
  height: auto;
  display: block;
}

/* Steps list */
.steps-list {
  margin: 32px 0;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.step-item {
  display: flex;
  gap: 20px;
  padding: 24px;
  background: #fafafa;
  border-radius: 16px;
  transition: transform 0.2s ease;
}

.step-item:hover {
  transform: translateX(4px);
}

.step-number {
  width: 36px;
  height: 36px;
  background: #1a1a1a;
  color: #fff;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  font-weight: 700;
  flex-shrink: 0;
}

.safedeal-steps .step-number {
  background: linear-gradient(135deg, #10b981 0%, #059669 100%);
}

.step-content h4 {
  font-size: 16px;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 6px;
}

.step-content p {
  font-size: 14px;
  color: #666;
  margin-bottom: 0;
  line-height: 1.6;
}

/* Bullet lists */
.bullet-list {
  margin: 16px 0 24px;
  padding-left: 24px;
}

.bullet-list li {
  font-size: 16px;
  color: #555;
  line-height: 1.8;
  margin-bottom: 8px;
}

/* Benefits grid */
.benefits-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
  margin: 32px 0;
}

.benefit-card {
  background: #fafafa;
  border-radius: 16px;
  padding: 28px;
}

.benefit-card h4 {
  font-size: 15px;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 16px;
}

.benefit-card ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.benefit-card li {
  font-size: 14px;
  color: #666;
  padding: 8px 0;
  border-bottom: 1px solid #eee;
}

.benefit-card li:last-child {
  border-bottom: none;
}

.highlight-text {
  font-size: 17px;
  color: #444;
  background: linear-gradient(90deg, #f0fdf4 0%, #ecfdf5 100%);
  padding: 24px;
  border-radius: 12px;
  border-left: 4px solid #42b883;
  margin-top: 32px;
}

/* Comparison table */
.comparison-table {
  margin: 32px 0;
  border-radius: 16px;
  overflow: hidden;
  border: 1px solid #eee;
}

.table-header {
  display: grid;
  grid-template-columns: 120px 1fr 1fr;
  background: #1a1a1a;
  padding: 16px 20px;
}

.th {
  font-size: 13px;
  font-weight: 600;
  color: #fff;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.table-row {
  display: grid;
  grid-template-columns: 120px 1fr 1fr;
  padding: 20px;
  border-bottom: 1px solid #eee;
}

.table-row:last-child {
  border-bottom: none;
}

.td {
  font-size: 14px;
  color: #555;
}

.platform-name {
  font-weight: 700;
}

.happay-name {
  color: #764ba2;
}

.safedeal-name {
  color: #059669;
}

.conclusion {
  font-size: 18px;
  color: #444;
  margin-top: 32px;
}

/* CTA */
.cta-section {
  margin-top: 80px;
}

.cta-card {
  background: linear-gradient(135deg, #1a1a1a 0%, #333 100%);
  border-radius: 24px;
  padding: 48px;
  text-align: center;
}

.cta-card h3 {
  font-family: 'DM Serif Display', serif;
  font-size: 28px;
  font-weight: 400;
  color: #fff;
  margin-top: 0;
  margin-bottom: 16px;
}

.cta-card p {
  font-size: 15px;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 24px;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 14px 32px;
  background: #42b883;
  color: #fff;
  font-size: 15px;
  font-weight: 600;
  border-radius: 100px;
  text-decoration: none;
  transition: background 0.2s ease;
}

.cta-button:hover {
  background: #38a373;
}

/* Responsive */
@media (max-width: 768px) {
  .blog-hero {
    padding: 120px 16px 60px;
  }
  
  .blog-content-wrapper {
    padding: 40px 16px 80px;
  }
  
  .benefits-grid {
    grid-template-columns: 1fr;
  }
  
  .table-header,
  .table-row {
    grid-template-columns: 1fr;
    gap: 8px;
  }
  
  .th:first-child,
  .td:first-child {
    display: none;
  }
  
  .step-item {
    flex-direction: column;
    gap: 12px;
  }
  
  .cta-card {
    padding: 32px 24px;
  }
}
</style>
