<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const headerRef = ref(null)
const logosRef = ref(null)
const stops = []

onMounted(() => {
  if (headerRef.value) {
    stops.push(
      inView(headerRef.value, ({ target }) => {
        animate(target, { opacity: [0, 1], y: [24, 0] }, { duration: 0.7, easing: [0.25, 0.1, 0.25, 1] })
      }, { amount: 0.2 })
    )
  }
  if (logosRef.value) {
    const items = logosRef.value.querySelectorAll('[data-stat]')
    stops.push(
      inView(logosRef.value, () => {
        animate(
          items,
          { opacity: [0, 1], y: [12, 0] },
          { duration: 0.5, delay: stagger(0.08, { start: 0.1 }), easing: [0.25, 0.1, 0.25, 1] }
        )
      }, { amount: 0.3 })
    )
  }
})

onUnmounted(() => stops.forEach((s) => s()))
</script>

<template>
  <section id="about" class="py-20 md:py-28 bg-light-bg">
    <div class="section-inner">
      <!-- Header: left heading + right description (matching PointOne Careers layout) -->
      <div ref="headerRef" style="opacity:0" class="mb-12">
        <span class="pill pill-dark mb-8 inline-block">About</span>
        <div class="flex flex-col md:flex-row md:items-start md:justify-between gap-8">
          <h2 class="heading-serif text-4xl sm:text-5xl md:text-[3.5rem] text-dark md:max-w-lg leading-tight">
            We're building the future of software
          </h2>
          <div class="md:max-w-md md:pt-2">
            <p class="text-sm text-dark/50 leading-relaxed mb-6">
              ByteLabs is a dev house and product studio specializing in custom software, web and mobile app development.
              We work with startups and businesses to turn ideas into polished, scalable digital products — and we're building our own along the way.
            </p>
            <a href="#contact" class="btn btn-sm btn-primary">Work with us</a>
          </div>
        </div>
      </div>

      <!-- Divider -->
      <div class="w-full h-px bg-black/6 my-14"></div>

      <!-- Stats row -->
      <div ref="logosRef" class="flex flex-wrap items-center justify-center gap-12 md:gap-20">
        <div data-stat style="opacity:0" class="text-center">
          <div class="heading-serif text-4xl text-dark">3+</div>
          <div class="text-sm text-dark/40 mt-1">Projects Delivered</div>
        </div>
        <div data-stat style="opacity:0" class="text-center">
          <div class="heading-serif text-4xl text-dark">1</div>
          <div class="text-sm text-dark/40 mt-1">In-house Product</div>
        </div>
        <div data-stat style="opacity:0" class="text-center">
          <div class="heading-serif text-4xl text-dark">8+</div>
          <div class="text-sm text-dark/40 mt-1">Technologies</div>
        </div>
        <div data-stat style="opacity:0" class="text-center">
          <div class="heading-serif text-4xl text-dark">100%</div>
          <div class="text-sm text-dark/40 mt-1">Client Satisfaction</div>
        </div>
      </div>
    </div>
  </section>
</template>
