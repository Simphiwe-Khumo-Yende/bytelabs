<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const headerRef = ref(null)
const cardsRef = ref(null)
const stops = []

onMounted(() => {
  if (headerRef.value) {
    stops.push(
      inView(headerRef.value, ({ target }) => {
        animate(target, { opacity: [0, 1], y: [24, 0] }, { duration: 0.7, easing: [0.25, 0.1, 0.25, 1] })
      }, { amount: 0.2 })
    )
  }
  if (cardsRef.value) {
    const cards = cardsRef.value.querySelectorAll('[data-project]')
    stops.push(
      inView(cardsRef.value, () => {
        animate(
          cards,
          { opacity: [0, 1], y: [20, 0] },
          { duration: 0.6, delay: stagger(0.1, { start: 0.1 }), easing: [0.25, 0.1, 0.25, 1] }
        )
      }, { amount: 0.1 })
    )
  }
})

onUnmounted(() => stops.forEach((s) => s()))
</script>

<template>
  <section id="work" class="py-20 md:py-28 bg-light-bg">
    <div class="section-inner">
      <!-- Header -->
      <div ref="headerRef" style="opacity:0" class="text-center mb-12">
        <span class="pill pill-light mb-6 inline-block">Our Work</span>
        <h2 class="heading-serif text-4xl sm:text-5xl md:text-6xl text-dark">
          Projects we've shipped
        </h2>
      </div>

      <!-- 2-column project cards (matching PointOne's Intelligence cards) -->
      <div ref="cardsRef" class="grid md:grid-cols-2 gap-4">
        <!-- Gaiosophy -->
        <div data-project style="opacity:0" class="feature-card-light">
          <div class="flex items-center gap-2 mb-1">
            <h3 class="text-base font-semibold text-dark">Gaiosophy</h3>
            <span class="text-[10px] font-medium text-emerald-600 bg-emerald-50 px-2 py-0.5 rounded-full">Delivered</span>
          </div>
          <p class="text-sm text-dark/50 leading-relaxed mb-6">
            A philosophy and wellness digital platform. Full-stack application with content management, user engagement, and a polished mobile-first experience.
          </p>
          <!-- Project mockup -->
          <div class="mt-auto rounded-xl bg-light-bg border border-black/4 p-4">
            <div class="flex items-center gap-2 mb-3">
              <div class="w-5 h-5 rounded bg-amber-100 flex items-center justify-center">
                <span class="text-[10px] text-amber-700 font-bold">G</span>
              </div>
              <span class="text-xs text-dark/50 font-medium">Gaiosophy Platform</span>
            </div>
            <div class="space-y-2">
              <div class="flex items-center justify-between p-2 bg-white rounded-lg">
                <span class="text-xs text-dark/60">Content Management</span>
                <span class="text-[10px] text-emerald-600">Active</span>
              </div>
              <div class="flex items-center justify-between p-2 bg-white rounded-lg">
                <span class="text-xs text-dark/60">User Dashboard</span>
                <span class="text-[10px] text-emerald-600">Active</span>
              </div>
            </div>
            <div class="flex gap-2 mt-3">
              <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Vue.js</span>
              <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Django</span>
              <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Tailwind</span>
            </div>
          </div>
        </div>

        <!-- StrikePoint -->
        <div data-project style="opacity:0" class="feature-card-light">
          <div class="flex items-center gap-2 mb-1">
            <h3 class="text-base font-semibold text-dark">StrikePoint</h3>
            <span class="text-[10px] font-medium text-emerald-600 bg-emerald-50 px-2 py-0.5 rounded-full">Delivered</span>
          </div>
          <p class="text-sm text-dark/50 leading-relaxed mb-6">
            A precision sports analytics platform with real-time data pipelines, interactive dashboards, and a cross-platform mobile app for athletes and coaches.
          </p>
          <!-- Resource allocation mockup (like PointOne's work allocation) -->
          <div class="mt-auto rounded-xl bg-light-bg border border-black/4 p-4">
            <div class="text-xs text-dark/40 mb-3 font-medium">Analytics Dashboard</div>
            <div class="space-y-2">
              <div class="flex items-center gap-3">
                <span class="text-xs text-dark/60 w-20">Athletes</span>
                <div class="flex gap-1 flex-1">
                  <div class="h-5 w-5 rounded bg-emerald-200"></div>
                  <div class="h-5 w-5 rounded bg-emerald-300"></div>
                  <div class="h-5 w-5 rounded bg-emerald-200"></div>
                  <div class="h-5 w-5 rounded bg-yellow-200"></div>
                  <div class="h-5 w-5 rounded bg-emerald-200"></div>
                </div>
              </div>
              <div class="flex items-center gap-3">
                <span class="text-xs text-dark/60 w-20">Coaches</span>
                <div class="flex gap-1 flex-1">
                  <div class="h-5 w-5 rounded bg-blue-200"></div>
                  <div class="h-5 w-5 rounded bg-emerald-200"></div>
                  <div class="h-5 w-5 rounded bg-blue-200"></div>
                  <div class="h-5 w-5 rounded bg-rose-200"></div>
                  <div class="h-5 w-5 rounded bg-emerald-200"></div>
                </div>
              </div>
            </div>
            <div class="flex gap-2 mt-3">
              <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Flutter</span>
              <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Dart</span>
              <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Firebase</span>
            </div>
          </div>
        </div>

        <!-- Happay (full width) -->
        <div data-project style="opacity:0" class="feature-card-light md:col-span-2">
          <div class="flex flex-col md:flex-row md:items-start gap-6">
            <div class="md:w-1/2">
              <div class="flex items-center gap-2 mb-1">
                <h3 class="text-base font-semibold text-dark">Happay</h3>
                <span class="text-[10px] font-medium text-blue-600 bg-blue-50 px-2 py-0.5 rounded-full">In Development</span>
              </div>
              <p class="text-sm text-dark/50 leading-relaxed mb-4">
                Our in-house fintech product — a modern application focused on simplifying payments and financial management for small businesses. Currently in active development.
              </p>
              <div class="flex gap-2">
                <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Flutter</span>
                <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Django</span>
                <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Firestore</span>
                <span class="text-[10px] text-dark/40 bg-dark/4 px-2 py-1 rounded">Tailwind</span>
              </div>
            </div>
            <!-- Payment mockup -->
            <div class="md:w-1/2 rounded-xl bg-light-bg border border-black/4 p-4">
              <div class="flex items-center justify-between mb-3">
                <span class="text-xs text-dark/50 font-medium">Transactions</span>
                <div class="h-6 w-16 bg-dark rounded-md flex items-center justify-center">
                  <span class="text-[10px] text-white">+ New</span>
                </div>
              </div>
              <div class="space-y-2">
                <div class="flex items-center justify-between p-2 bg-white rounded-lg">
                  <div class="flex items-center gap-2">
                    <div class="w-4 h-4 rounded-full bg-emerald-100"></div>
                    <span class="text-xs text-dark/60">Payment received</span>
                  </div>
                  <span class="text-xs font-medium text-emerald-600">+R1,200</span>
                </div>
                <div class="flex items-center justify-between p-2 bg-white rounded-lg">
                  <div class="flex items-center gap-2">
                    <div class="w-4 h-4 rounded-full bg-rose-100"></div>
                    <span class="text-xs text-dark/60">Subscription fee</span>
                  </div>
                  <span class="text-xs font-medium text-rose-600">-R350</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
