<script setup>
import { ref, reactive, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const sectionRef = ref(null)
const form = reactive({ name: '', email: '', company: '', budget: '', message: '' })
const status = ref('idle') // idle | sending | sent | error
const errorMsg = ref('')

const API_URL = import.meta.env.VITE_CONTACT_API || 'https://bytelabs-contact-api.onrender.com'

async function handleSubmit() {
  status.value = 'sending'
  errorMsg.value = ''

  try {
    const res = await fetch(`${API_URL}/contact`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        name: form.name,
        email: form.email,
        company: form.company,
        budget: form.budget,
        message: form.message
      })
    })

    if (!res.ok) throw new Error('Failed to send')

    status.value = 'sent'
    Object.assign(form, { name: '', email: '', company: '', budget: '', message: '' })

    setTimeout(() => { status.value = 'idle' }, 5000)
  } catch (e) {
    status.value = 'error'
    errorMsg.value = 'Something went wrong. Please try again or email us directly.'
    setTimeout(() => { status.value = 'idle' }, 4000)
  }
}

onMounted(() => {
  if (!sectionRef.value) return
  inView(sectionRef.value, () => {
    const items = sectionRef.value.querySelectorAll('[data-animate]')
    animate(
      items,
      { opacity: [0, 1], y: [24, 0] },
      { duration: 0.7, delay: stagger(0.08), easing: [0.25, 0.1, 0.25, 1] }
    )
  }, { amount: 0.05 })
})
</script>

<template>
  <div ref="sectionRef" class="contact-page">
    <!-- Hero -->
    <section class="contact-hero">
      <div class="section-inner">
        <div data-animate style="opacity:0" class="hero-text">
          <span class="pill pill-light">Contact</span>
          <h1 class="heading-serif hero-title">
            Let's talk about your project
          </h1>
          <p class="hero-subtitle">
            Have an idea you'd like to bring to life? Fill out the form below and we'll get back to you within 24 hours.
          </p>
        </div>
      </div>
    </section>

    <!-- Form section -->
    <section class="pb-20 md:pb-28">
      <div class="section-inner" style="max-width:720px;">
        <div data-animate style="opacity:0" class="contact-card">
          <form @submit.prevent="handleSubmit" class="contact-form">
            <div class="form-row">
              <div class="form-group">
                <label>Name</label>
                <input v-model="form.name" type="text" required placeholder="Your full name" class="input-field" />
              </div>
              <div class="form-group">
                <label>Email</label>
                <input v-model="form.email" type="email" required placeholder="you@company.com" class="input-field" />
              </div>
            </div>

            <div class="form-row">
              <div class="form-group">
                <label>Company <span class="optional">(optional)</span></label>
                <input v-model="form.company" type="text" placeholder="Your company" class="input-field" />
              </div>
              <div class="form-group">
                <label>Budget <span class="optional">(optional)</span></label>
                <select v-model="form.budget" class="input-field">
                  <option value="" disabled selected>Select range</option>
                  <option value="< R20k">Less than R20k</option>
                  <option value="R20k – R50k">R20k – R50k</option>
                  <option value="R50k – R100k">R50k – R100k</option>
                  <option value="R100k+">R100k+</option>
                </select>
              </div>
            </div>

            <div class="form-group">
              <label>Message</label>
              <textarea
                v-model="form.message"
                rows="5"
                required
                placeholder="Tell us about your project, goals, and timeline..."
                class="input-field resize-none"
              />
            </div>

            <button
              type="submit"
              class="btn btn-lg btn-primary w-full"
              :disabled="status === 'sending' || status === 'sent'"
            >
              <template v-if="status === 'idle'">Send Message</template>
              <template v-else-if="status === 'sending'">
                <svg class="animate-spin mr-2" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2v4M12 18v4M4.93 4.93l2.83 2.83M16.24 16.24l2.83 2.83M2 12h4M18 12h4M4.93 19.07l2.83-2.83M16.24 7.76l2.83-2.83"/></svg>
                Sending...
              </template>
              <template v-else-if="status === 'sent'">Message Sent!</template>
              <template v-else>Try Again</template>
            </button>

            <!-- Success message -->
            <transition
              enter-active-class="transition duration-300 ease-out"
              enter-from-class="opacity-0 translate-y-2"
              enter-to-class="opacity-100 translate-y-0"
              leave-active-class="transition duration-200 ease-in"
              leave-from-class="opacity-100"
              leave-to-class="opacity-0"
            >
              <p v-if="status === 'sent'" class="status-msg success">
                Thanks! We'll be in touch soon.
              </p>
              <p v-else-if="status === 'error'" class="status-msg error">
                {{ errorMsg }}
              </p>
            </transition>
          </form>
        </div>

        <!-- Alt contact info -->
        <div data-animate style="opacity:0" class="alt-contact">
          <p>Prefer email? Reach us at
            <a href="mailto:bytelabs@happay.co.za" class="text-dark font-medium underline decoration-dark/20 underline-offset-4 hover:decoration-dark transition-colors">
              bytelabs@happay.co.za
            </a>
          </p>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.contact-page {
  padding-top: 120px;
}

.contact-hero {
  padding-bottom: 3rem;
}

.hero-text {
  text-align: center;
  max-width: 640px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.hero-title {
  font-size: 2.5rem;
  color: var(--color-dark);
  margin-bottom: 1rem;
}

@media (min-width: 640px) {
  .hero-title { font-size: 3rem; }
}

.hero-subtitle {
  font-size: 0.95rem;
  color: rgba(24, 26, 28, 0.45);
  line-height: 1.6;
  max-width: 480px;
}

.contact-card {
  background: var(--color-light-bg);
  border: 1px solid rgba(24, 26, 28, 0.04);
  border-radius: 20px;
  padding: 2rem;
}

@media (min-width: 640px) {
  .contact-card { padding: 2.5rem; }
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .form-row { grid-template-columns: 1fr 1fr; }
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}

.form-group label {
  font-size: 12px;
  font-weight: 500;
  color: rgba(24, 26, 28, 0.45);
}

.form-group .optional {
  font-weight: 400;
  color: rgba(24, 26, 28, 0.3);
}

.form-group select.input-field {
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg width='10' height='6' viewBox='0 0 10 6' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1l4 4 4-4' stroke='%23999' stroke-width='1.5' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 14px center;
  padding-right: 2.5rem;
}

.status-msg {
  text-align: center;
  font-size: 14px;
  font-weight: 500;
  margin-top: 0.5rem;
}

.status-msg.success { color: #16a34a; }
.status-msg.error { color: #dc2626; }

.alt-contact {
  text-align: center;
  margin-top: 2rem;
  font-size: 14px;
  color: rgba(24, 26, 28, 0.4);
}

@keyframes spin {
  to { transform: rotate(360deg); }
}
.animate-spin {
  animation: spin 1s linear infinite;
}
</style>
