<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate, inView } from 'motion'

const cardRef = ref(null)
const form = ref({ name: '', email: '', message: '' })
const submitted = ref(false)
const stops = []

function handleSubmit() {
  submitted.value = true
  setTimeout(() => {
    form.value = { name: '', email: '', message: '' }
    submitted.value = false
  }, 3000)
}

onMounted(() => {
  if (cardRef.value) {
    stops.push(
      inView(cardRef.value, ({ target }) => {
        animate(target, { opacity: [0, 1], y: [24, 0] }, { duration: 0.7, easing: [0.25, 0.1, 0.25, 1] })
      }, { amount: 0.15 })
    )
  }
})

onUnmounted(() => stops.forEach((s) => s()))
</script>

<template>
  <section id="contact" class="py-20 md:py-28 bg-white">
    <div class="section-inner">
      <div ref="cardRef" style="opacity:0" class="rounded-2xl bg-light-bg border border-black/4 overflow-hidden">
        <div class="grid md:grid-cols-2 gap-0">
          <!-- Left: CTA text -->
          <div class="p-8 md:p-12 flex flex-col justify-center">
            <span class="pill pill-light mb-6 inline-block w-fit">Get in Touch</span>
            <h2 class="heading-serif text-3xl sm:text-4xl text-dark mb-4">
              Let's build something great together
            </h2>
            <p class="text-sm text-dark/50 leading-relaxed mb-6">
              Whether you have a project in mind or just want to explore possibilities — we'd love to hear from you.
            </p>
            <a
              href="mailto:hello@bytelabs.dev"
              class="text-sm font-medium text-dark underline decoration-dark/20 underline-offset-4 hover:decoration-dark transition-colors"
            >
              hello@bytelabs.dev
            </a>
          </div>

          <!-- Right: form -->
          <div class="p-8 md:p-12 bg-white">
            <form @submit.prevent="handleSubmit" class="flex flex-col gap-4">
              <div>
                <label class="text-xs font-medium text-dark/50 mb-1.5 block">Name</label>
                <input v-model="form.name" type="text" required class="input-field" placeholder="Your name" />
              </div>
              <div>
                <label class="text-xs font-medium text-dark/50 mb-1.5 block">Email</label>
                <input v-model="form.email" type="email" required class="input-field" placeholder="you@company.com" />
              </div>
              <div>
                <label class="text-xs font-medium text-dark/50 mb-1.5 block">Message</label>
                <textarea v-model="form.message" rows="4" required class="input-field resize-none" placeholder="Tell us about your project..." />
              </div>
              <button type="submit" class="btn btn-lg btn-primary w-full mt-2" :disabled="submitted">
                {{ submitted ? 'Message Sent!' : 'Send Message' }}
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
