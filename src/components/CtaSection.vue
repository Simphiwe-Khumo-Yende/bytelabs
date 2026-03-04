<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate, inView } from 'motion'

const cardRef = ref(null)
const stops = []

onMounted(() => {
  if (cardRef.value) {
    stops.push(
      inView(cardRef.value, ({ target }) => {
        animate(
          target,
          { opacity: [0, 1], scale: [0.96, 1], y: [16, 0] },
          { duration: 0.7, easing: [0.25, 0.1, 0.25, 1] }
        )
      }, { amount: 0.3 })
    )
  }
})

onUnmounted(() => stops.forEach((s) => s()))
</script>

<template>
  <section class="py-16 md:py-20 bg-light-bg">
    <div class="section-inner">
      <!-- CTA card (matching PointOne's "Get Started" card with gradient top edge) -->
      <div
        ref="cardRef"
        style="opacity:0"
        class="relative rounded-2xl bg-white border border-black/4 p-12 md:p-20 text-center overflow-hidden"
      >
        <!-- Subtle gradient line at top -->
        <div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-black/8 to-transparent"></div>

        <span class="pill pill-light mb-6 inline-block">Get Started</span>
        <h3 class="heading-serif text-3xl sm:text-4xl md:text-5xl text-dark mb-8">
          Ready to bring your idea to life?
        </h3>
        <a href="#contact" class="btn btn-lg btn-primary">Start a Project</a>
      </div>
    </div>
  </section>
</template>
