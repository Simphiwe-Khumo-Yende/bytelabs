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
    const cards = cardsRef.value.querySelectorAll('[data-tech]')
    stops.push(
      inView(cardsRef.value, () => {
        animate(
          cards,
          { opacity: [0, 1], y: [20, 0] },
          { duration: 0.6, delay: stagger(0.1, { start: 0.1 }), easing: [0.25, 0.1, 0.25, 1] }
        )
      }, { amount: 0.15 })
    )
  }
})

onUnmounted(() => stops.forEach((s) => s()))

const techIcons = [
  { name: 'Vue.js', letter: 'V', color: 'bg-emerald-100 text-emerald-700' },
  { name: 'Python', letter: 'Py', color: 'bg-blue-100 text-blue-700' },
  { name: 'Flutter', letter: 'F', color: 'bg-sky-100 text-sky-700' },
  { name: 'Django', letter: 'Dj', color: 'bg-green-100 text-green-800' },
  { name: 'Tailwind', letter: 'Tw', color: 'bg-cyan-100 text-cyan-700' },
  { name: 'Dart', letter: 'D', color: 'bg-blue-100 text-blue-600' },
  { name: 'Firebase', letter: '🔥', color: 'bg-amber-100 text-amber-700' },
  { name: 'JavaScript', letter: 'JS', color: 'bg-yellow-100 text-yellow-700' },
  { name: 'PostgreSQL', letter: 'PG', color: 'bg-indigo-100 text-indigo-700' },
  { name: 'HTML5', letter: 'H5', color: 'bg-orange-100 text-orange-700' },
  { name: 'Git', letter: 'G', color: 'bg-red-100 text-red-600' },
  { name: 'Docker', letter: 'D', color: 'bg-blue-100 text-blue-600' },
]

const integrations = [
  { name: 'Firestore', letter: 'F' },
  { name: 'Cloud Functions', letter: 'CF' },
  { name: 'REST APIs', letter: 'R' },
  { name: 'GraphQL', letter: 'GQ' },
  { name: 'AWS', letter: 'A' },
  { name: 'Vercel', letter: 'V' },
  { name: 'GitHub', letter: 'GH' },
  { name: 'Figma', letter: 'Fi' },
]
</script>

<template>
  <section class="py-20 md:py-28 bg-white">
    <div class="section-inner">
      <!-- Separator line -->
      <div class="w-full h-px bg-black/6 mb-16"></div>

      <!-- Header -->
      <div ref="headerRef" style="opacity:0" class="text-center mb-12">
        <span class="pill pill-light mb-6 inline-block">Tech Stack</span>
        <h2 class="heading-serif text-4xl sm:text-5xl md:text-6xl text-dark">
          Works everywhere you do
        </h2>
      </div>

      <!-- 2-column cards (matching PointOne's Integrations layout) -->
      <div ref="cardsRef" class="grid md:grid-cols-2 gap-4">
        <!-- Left: Tech icon grid -->
        <div data-tech style="opacity:0" class="feature-card-light">
          <h3 class="text-base font-semibold text-dark mb-1">Built with proven technologies</h3>
          <p class="text-sm text-dark/50 leading-relaxed mb-6">
            We use modern, battle-tested frameworks and languages — from Vue.js and Flutter to Django and Firebase.
          </p>
          <!-- Icon grid (matching PointOne's app icon grid) -->
          <div class="mt-auto grid grid-cols-4 gap-3">
            <div
              v-for="tech in techIcons"
              :key="tech.name"
              class="aspect-square rounded-2xl border border-black/4 bg-white flex flex-col items-center justify-center gap-1 hover:scale-105 transition-transform"
            >
              <div class="w-8 h-8 rounded-lg flex items-center justify-center text-xs font-bold" :class="tech.color">
                {{ tech.letter }}
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Integrations list (matching PointOne's billing software list) -->
        <div data-tech style="opacity:0" class="feature-card-light">
          <h3 class="text-base font-semibold text-dark mb-1">Seamless integrations</h3>
          <p class="text-sm text-dark/50 leading-relaxed mb-6">
            We connect with the tools and platforms your business already relies on.
          </p>
          <!-- ByteLabs logo + integration list -->
          <div class="mt-auto rounded-xl bg-light-bg border border-black/4 p-5">
            <div class="flex items-center gap-2 mb-5">
              <div class="w-8 h-8 rounded-lg bg-dark flex items-center justify-center">
                <span class="text-white text-xs font-bold">B</span>
              </div>
            </div>
            <div class="grid grid-cols-2 gap-x-6 gap-y-3">
              <div
                v-for="item in integrations"
                :key="item.name"
                class="flex items-center justify-between"
              >
                <div class="flex items-center gap-2">
                  <div class="w-5 h-5 rounded bg-light-bg border border-black/6 flex items-center justify-center">
                    <span class="text-[8px] text-dark/50 font-bold">{{ item.letter }}</span>
                  </div>
                  <span class="text-sm font-medium text-dark">{{ item.name }}</span>
                </div>
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none">
                  <path d="M20 6L9 17l-5-5" stroke="#22c55e" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
