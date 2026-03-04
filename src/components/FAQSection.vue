<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const sectionRef = ref(null)
const openIndex = ref(0)

const faqs = [
  {
    question: 'How much does a typical project cost?',
    answer: 'Project costs vary based on complexity and scope. A simple landing page might start at R15,000, while a full-featured mobile app or web platform typically ranges from R80,000 to R250,000+. We provide detailed quotes after our discovery call—no surprises.'
  },
  {
    question: 'How long does it take to build a product?',
    answer: 'Most MVPs take 6-10 weeks from kickoff to launch. Simple websites can be done in 2-3 weeks. Complex platforms with multiple integrations may take 3-4 months. We\'ll give you a realistic timeline upfront and keep you updated throughout.'
  },
  {
    question: 'Do you work with startups or only established businesses?',
    answer: 'We work with both! We love helping startups bring their first product to market, and we also partner with established companies on new features or complete rebuilds. If you have a clear vision and budget, we\'re ready to build.'
  },
  {
    question: 'What happens after launch?',
    answer: 'We don\'t disappear after deployment. We offer ongoing support packages for maintenance, bug fixes, and feature updates. Many clients come back monthly for continuous improvements based on user feedback.'
  },
  {
    question: 'Can you work with my existing team or codebase?',
    answer: 'Absolutely. We can augment your team, take over an existing project, or work alongside your developers. We follow clean code practices and document everything for smooth collaboration.'
  },
  {
    question: 'What technologies do you specialize in?',
    answer: 'Our core stack includes Vue.js and Tailwind CSS for web frontends, Flutter for cross-platform mobile apps, and Django/Python for backends. We also work with Firebase, PostgreSQL, and various cloud platforms depending on project needs.'
  }
]

function toggle(index) {
  openIndex.value = openIndex.value === index ? -1 : index
}

onMounted(() => {
  if (!sectionRef.value) return
  
  inView(sectionRef.value, () => {
    const items = sectionRef.value.querySelectorAll('[data-animate]')
    animate(
      items,
      { opacity: [0, 1], y: [30, 0] },
      { duration: 0.6, delay: stagger(0.08), easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.2 })
})
</script>

<template>
  <section class="faq-section">
    <div ref="sectionRef" class="section-container">
      <div class="faq-layout">
        <div data-animate class="faq-header">
          <span class="section-label">FAQ</span>
          <h2 class="section-heading">Common questions</h2>
          <p class="section-subheading">Everything you need to know before starting a project with ByteLabs.</p>
          
          <a href="#contact" class="contact-link">
            Still have questions?
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M5 12h14"/>
              <path d="m12 5 7 7-7 7"/>
            </svg>
          </a>
        </div>

        <div class="faq-list">
          <div 
            v-for="(faq, index) in faqs" 
            :key="index"
            data-animate
            class="faq-item"
            :class="{ 'is-open': openIndex === index }"
          >
            <button class="faq-question" @click="toggle(index)">
              <span>{{ faq.question }}</span>
              <div class="faq-icon">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M12 5v14"/>
                  <path d="M5 12h14"/>
                </svg>
              </div>
            </button>
            <div class="faq-answer">
              <p>{{ faq.answer }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.faq-section {
  background: #f5f5f7;
  padding: 120px 24px;
}

.section-container {
  max-width: 1100px;
  margin: 0 auto;
}

.faq-layout {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 80px;
  align-items: start;
}

.faq-header {
  position: sticky;
  top: 120px;
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
  font-size: clamp(2rem, 4vw, 2.5rem);
  font-weight: 400;
  color: #1a1a1a;
  letter-spacing: -0.02em;
  margin-bottom: 16px;
}

.section-subheading {
  font-size: 15px;
  color: #888;
  line-height: 1.6;
  margin-bottom: 32px;
}

.contact-link {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 14px;
  font-weight: 600;
  color: #1a1a1a;
  text-decoration: none;
  transition: color 0.2s ease;
}

.contact-link:hover {
  color: #42b883;
}

.faq-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.faq-item {
  background: #fff;
  border-radius: 16px;
  overflow: hidden;
  transition: box-shadow 0.3s ease;
}

.faq-item:hover {
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.04);
}

.faq-question {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  padding: 24px;
  background: none;
  border: none;
  text-align: left;
  cursor: pointer;
  font-size: 16px;
  font-weight: 600;
  color: #1a1a1a;
  line-height: 1.4;
}

.faq-icon {
  flex-shrink: 0;
  width: 32px;
  height: 32px;
  background: #f5f5f7;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #888;
  transition: all 0.3s ease;
}

.faq-item.is-open .faq-icon {
  background: #42b883;
  color: #fff;
  transform: rotate(45deg);
}

.faq-answer {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease, padding 0.3s ease;
}

.faq-item.is-open .faq-answer {
  max-height: 300px;
}

.faq-answer p {
  padding: 0 24px 24px;
  font-size: 14px;
  color: #666;
  line-height: 1.7;
}

/* Responsive */
@media (max-width: 900px) {
  .faq-layout {
    grid-template-columns: 1fr;
    gap: 48px;
  }
  
  .faq-header {
    position: static;
    text-align: center;
  }
}

@media (max-width: 640px) {
  .faq-section {
    padding: 80px 16px;
  }
  
  .faq-question {
    padding: 20px;
    font-size: 15px;
  }
  
  .faq-answer p {
    padding: 0 20px 20px;
  }
}
</style>
