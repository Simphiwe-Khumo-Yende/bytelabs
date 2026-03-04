<script setup>
import { ref, onMounted } from 'vue'
import { animate, inView } from 'motion'

const sectionRef = ref(null)

onMounted(() => {
  if (!sectionRef.value) return
  
  inView(sectionRef.value, () => {
    const items = sectionRef.value.querySelectorAll('[data-animate]')
    animate(
      items,
      { opacity: [0, 1], y: [30, 0] },
      { duration: 0.6, delay: 0.1, easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.2 })
})
</script>

<template>
  <div ref="sectionRef" class="footer-wrapper">
    <!-- CTA Section -->
    <section data-animate class="cta-section">
      <div class="cta-badge">Get Started</div>
      <h2 class="cta-heading">Let's build something great.</h2>
      <a href="#contact" class="cta-button">Start a Project</a>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="footer-brand">
        <div class="footer-logo-icon">
        </div>
        <span class="footer-brand-name">ByteLabs()</span>
      </div>

      <div class="footer-columns">
        <!-- Services -->
        <div class="footer-column">
          <span class="footer-column-title">Services</span>
          <ul>
            <li><a href="#services">Web Development</a></li>
            <li><a href="#services">Mobile Apps</a></li>
            <li><a href="#services">UI/UX Design</a></li>
            <li><a href="#services">Backend Systems</a></li>
          </ul>
        </div>

        <!-- Projects -->
        <div class="footer-column">
          <span class="footer-column-title">Projects</span>
          <ul>
            <li><a href="#work">Gaiosophy</a></li>
            <li><a href="#work">StrikePoint</a></li>
            <li><a href="#work">Happay</a></li>
            <li><a href="#work">SafeDeal</a></li>
          </ul>
        </div>

        <!-- Company -->
        <div class="footer-column">
          <span class="footer-column-title">Company</span>
          <ul>
            <li><a href="#about">About</a></li>
            <li><a href="#">Careers</a></li>
          </ul>
        </div>

        <!-- Contact -->
        <div class="footer-column">
          <span class="footer-column-title">Contact</span>
          <ul>
            <li><a href="mailto:hello@bytelabs.dev">hello@bytelabs.dev</a></li>
            <li><a href="tel:+27646116075">+27 64 611 6075</a></li>
            <li><span class="footer-address">807 Ndlovu St, Soshanguve<br>Block DD, Pretoria, 0152</span></li>
          </ul>
        </div>
      </div>
    </footer>

    <div class="footer-bottom">
      <span class="copyright">© 2026 ByteLabs. All rights reserved.</span>
    </div>
  </div>
</template>

<style scoped>
.footer-wrapper {
  background: #f5f5f7;
  padding: 60px 24px 40px;
}

/* CTA Section */
.cta-section {
  background: #fff;
  border-radius: 28px;
  padding: 70px 40px 80px;
  max-width: 1100px;
  width: 100%;
  margin: 0 auto 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.cta-badge {
  display: inline-flex;
  align-items: center;
  padding: 8px 20px;
  border: 1px solid #ddd;
  border-radius: 100px;
  font-size: 14px;
  font-weight: 500;
  color: #1a1a1a;
  background: #fff;
  margin-bottom: 32px;
}

.cta-heading {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2.5rem, 6vw, 3.5rem);
  font-weight: 400;
  color: #1a1a1a;
  letter-spacing: -0.02em;
  line-height: 1.1;
  margin-bottom: 32px;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 16px 32px;
  background: #1a1a1a;
  color: #fff;
  font-size: 15px;
  font-weight: 600;
  border-radius: 100px;
  text-decoration: none;
  border: none;
  cursor: pointer;
  transition: background 0.15s ease;
}

.cta-button:hover {
  background: #333;
}

/* Footer */
.footer {
  max-width: 1100px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  padding: 0 20px;
}

.footer-brand {
  display: flex;
  align-items: center;
  gap: 8px;
}

.footer-logo-icon {
  display: flex;
  align-items: center;
  gap: 2px;
}

.logo-dot {
  width: 8px;
  height: 8px;
  background: #1a1a1a;
  border-radius: 50%;
}

.logo-line {
  width: 4px;
  height: 20px;
  background: #1a1a1a;
  border-radius: 2px;
}

.footer-brand-name {
  font-size: 17px;
  font-weight: 700;
  color: #1a1a1a;
  letter-spacing: -0.3px;
}

.footer-columns {
  display: flex;
  gap: 60px;
}

.footer-column {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.footer-column-title {
  font-size: 13px;
  font-weight: 500;
  color: #999;
  margin-bottom: 16px;
}

.footer-column ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 0;
  margin: 0;
}

.footer-column ul li a {
  font-size: 15px;
  font-weight: 500;
  color: #1a1a1a;
  text-decoration: none;
  transition: color 0.15s ease;
}

.footer-column ul li a:hover {
  color: #666;
}

.footer-address {
  font-size: 14px;
  font-weight: 400;
  color: #666;
  line-height: 1.5;
}

/* Footer bottom */
.footer-bottom {
  max-width: 1100px;
  width: 100%;
  margin: 48px auto 0;
  padding: 24px 20px 0;
  border-top: 1px solid rgba(0, 0, 0, 0.08);
  text-align: center;
}

.copyright {
  font-size: 13px;
  color: #999;
}

/* Mobile responsive */
@media (max-width: 900px) {
  .footer {
    flex-direction: column;
    gap: 40px;
  }
  
  .footer-columns {
    flex-wrap: wrap;
    gap: 40px 48px;
  }
}

@media (max-width: 640px) {
  .footer-wrapper {
    padding: 40px 16px 32px;
  }
  
  .cta-section {
    padding: 50px 24px 60px;
    border-radius: 20px;
    margin-bottom: 48px;
  }
  
  .cta-badge {
    padding: 6px 16px;
    font-size: 13px;
    margin-bottom: 24px;
  }
  
  .cta-heading {
    margin-bottom: 24px;
  }
  
  .cta-button {
    padding: 14px 28px;
    font-size: 14px;
  }
  
  .footer {
    padding: 0;
  }
  
  .footer-columns {
    gap: 32px 40px;
  }
  
  .footer-column-title {
    font-size: 12px;
    margin-bottom: 12px;
  }
  
  .footer-column ul {
    gap: 10px;
  }
  
  .footer-column ul li a {
    font-size: 14px;
  }
  
  .footer-bottom {
    margin-top: 36px;
    padding-top: 20px;
  }
}
</style>
