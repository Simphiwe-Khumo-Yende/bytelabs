<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate, stagger, inView } from 'motion'

const sectionRef = ref(null)
const stops = []

onMounted(() => {
  if (!sectionRef.value) return

  const header = sectionRef.value.querySelector('[data-section-header]')
  if (header) {
    stops.push(
      inView(header, ({ target }) => {
        animate(target, { opacity: [0, 1], y: [24, 0] }, { duration: 0.7, easing: [0.25, 0.1, 0.25, 1] })
      }, { amount: 0.2 })
    )
  }

  const cards = sectionRef.value.querySelectorAll('[data-card]')
  if (cards.length) {
    stops.push(
      inView(sectionRef.value.querySelector('[data-grid]'), () => {
        animate(
          cards,
          { opacity: [0, 1], y: [24, 0] },
          { duration: 0.6, delay: stagger(0.1, { start: 0.15 }), easing: [0.25, 0.1, 0.25, 1] }
        )
      }, { amount: 0.08 })
    )
  }
})

onUnmounted(() => stops.forEach((s) => s()))
</script>

<template>
  <section id="services" ref="sectionRef" class="bg-dark py-20 md:py-28">
    <div class="section-inner">
      <!-- Header -->
      <div data-section-header style="opacity:0" class="text-center mb-14">
        <span class="pill pill-dark mb-5 inline-block">Services</span>
        <h2 class="heading-serif text-4xl sm:text-5xl md:text-6xl text-light">
          Everything you need<br class="hidden sm:block"> to ship great software
        </h2>
      </div>

      <!-- Feature cards -->
      <div data-grid class="grid md:grid-cols-2 gap-5">
        <!-- Vue.js & Tailwind CSS -->
        <div data-card style="opacity:0" class="feature-card">
          <h3 class="text-base font-semibold text-light mb-2">Vue.js & Tailwind CSS</h3>
          <p class="text-sm text-light/50 leading-relaxed mb-6">
            Component-driven UI with utility-first styling for rapid iteration and pixel-perfect design.
          </p>
          <div class="mt-auto rounded-xl bg-white/3 border border-white/5 p-4">
            <div class="flex items-center gap-2 mb-3">
              <div class="w-6 h-6 rounded bg-emerald-500/20 flex items-center justify-center">
                <span class="text-[10px] text-emerald-400 font-bold">V</span>
              </div>
              <span class="text-xs text-light/60 font-medium">Component Library</span>
            </div>
            <div class="space-y-2">
              <div class="flex items-center gap-2">
                <div class="h-6 flex-1 bg-white/5 rounded"></div>
                <div class="h-6 w-12 bg-white/5 rounded"></div>
              </div>
              <div class="flex items-center gap-2">
                <div class="h-6 flex-1 bg-white/5 rounded"></div>
                <div class="h-6 w-12 bg-white/5 rounded"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Django backend -->
        <div data-card style="opacity:0" class="feature-card">
          <h3 class="text-base font-semibold text-light mb-2">Django backend</h3>
          <p class="text-sm text-light/50 leading-relaxed mb-6">
            Python-powered APIs with built-in security, admin panels, and ORM for robust data management.
          </p>
          <div class="mt-auto rounded-xl bg-white/3 border border-white/5 p-4">
            <div class="space-y-3">
              <div class="flex items-center gap-3">
                <div class="w-6 h-6 rounded-full bg-blue-500/20 flex items-center justify-center">
                  <span class="text-[10px] text-blue-400">1</span>
                </div>
                <span class="text-xs text-light/60">API Gateway</span>
                <div class="flex-1"></div>
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none"><path d="M5 12h14" stroke="rgba(255,255,255,0.2)" stroke-width="1.5"/></svg>
              </div>
              <div class="flex items-center gap-3">
                <div class="w-6 h-6 rounded-full bg-violet-500/20 flex items-center justify-center">
                  <span class="text-[10px] text-violet-400">2</span>
                </div>
                <span class="text-xs text-light/60">Django ORM</span>
                <div class="flex-1"></div>
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none"><path d="M5 12h14" stroke="rgba(255,255,255,0.2)" stroke-width="1.5"/></svg>
              </div>
              <div class="flex items-center gap-3">
                <div class="w-6 h-6 rounded-full bg-amber-500/20 flex items-center justify-center">
                  <span class="text-[10px] text-amber-400">3</span>
                </div>
                <span class="text-xs text-light/60">Database</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Flutter & Dart -->
        <div data-card :style="{ opacity: 0, background: 'linear-gradient(135deg, rgba(16,80,60,0.25) 0%, rgba(255,255,255,0.02) 100%)' }" class="feature-card">
          <h3 class="text-base font-semibold text-light mb-2">Flutter & Dart</h3>
          <p class="text-sm text-light/50 leading-relaxed mb-6">
            Single codebase for iOS and Android with native performance. Beautiful, responsive UIs with hot reload.
          </p>
          <div class="mt-auto flex justify-center">
            <div class="w-36 rounded-2xl bg-white/5 border border-white/8 p-3">
              <div class="h-3 w-10 mx-auto bg-white/10 rounded-full mb-3"></div>
              <div class="space-y-2">
                <div class="h-10 bg-white/5 rounded-lg"></div>
                <div class="h-5 bg-white/5 rounded-lg"></div>
                <div class="h-5 bg-white/5 rounded-lg"></div>
                <div class="h-7 bg-blue-500/20 rounded-lg"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Firebase integration -->
        <div data-card style="opacity:0" class="feature-card">
          <h3 class="text-base font-semibold text-light mb-2">Firebase integration</h3>
          <p class="text-sm text-light/50 leading-relaxed mb-6">
            Real-time databases, authentication, and cloud functions. Ship faster with managed infrastructure.
          </p>
          <div class="mt-auto rounded-xl bg-white/3 border border-white/5 p-4">
            <div class="flex items-center gap-2 mb-3">
              <div class="w-5 h-5 rounded bg-amber-500/20 flex items-center justify-center">
                <span class="text-[9px] text-amber-400">🔥</span>
              </div>
              <span class="text-xs text-light/50 font-medium">Firebase Console</span>
            </div>
            <div class="grid grid-cols-2 gap-2">
              <div class="p-2 rounded bg-white/3 text-center">
                <div class="text-lg font-bold text-light">2.4k</div>
                <div class="text-[10px] text-light/40">Active Users</div>
              </div>
              <div class="p-2 rounded bg-white/3 text-center">
                <div class="text-lg font-bold text-light">99.9%</div>
                <div class="text-[10px] text-light/40">Uptime</div>
              </div>
            </div>
          </div>
        </div>

        <!-- System architecture -->
        <div data-card style="opacity:0" class="feature-card">
          <h3 class="text-base font-semibold text-light mb-2">System architecture</h3>
          <p class="text-sm text-light/50 leading-relaxed mb-6">
            Scalable designs using microservices, queues, and event-driven patterns that grow with your business.
          </p>
          <div class="mt-auto rounded-xl bg-white/3 border border-white/5 p-4">
            <div class="grid grid-cols-2 gap-x-4 gap-y-3">
              <div>
                <div class="text-[10px] text-light/30 mb-1">Type</div>
                <div class="text-xs text-light/70">Microservices</div>
              </div>
              <div>
                <div class="text-[10px] text-light/30 mb-1">Scale</div>
                <div class="text-xs text-light/70">Auto-scaling</div>
              </div>
              <div>
                <div class="text-[10px] text-light/30 mb-1">Deployment</div>
                <div class="text-xs text-light/70">CI/CD Pipeline</div>
              </div>
              <div>
                <div class="text-[10px] text-light/30 mb-1">Monitoring</div>
                <div class="text-xs text-light/70">Real-time</div>
              </div>
            </div>
          </div>
        </div>

        <!-- API development -->
        <div data-card style="opacity:0" class="feature-card">
          <h3 class="text-base font-semibold text-light mb-2">API development</h3>
          <p class="text-sm text-light/50 leading-relaxed mb-6">
            RESTful and GraphQL APIs built for performance, developer experience, and seamless third-party integrations.
          </p>
          <div class="mt-auto rounded-xl bg-white/3 border border-white/5 p-4">
            <div class="space-y-2">
              <div class="flex items-center justify-between">
                <span class="text-xs text-light/50">GET /api/projects</span>
                <span class="text-[10px] text-emerald-400 bg-emerald-500/10 px-2 py-0.5 rounded">200 OK</span>
              </div>
              <div class="flex items-center justify-between">
                <span class="text-xs text-light/50">POST /api/deploy</span>
                <span class="text-[10px] text-emerald-400 bg-emerald-500/10 px-2 py-0.5 rounded">201</span>
              </div>
              <div class="flex items-center justify-between">
                <span class="text-xs text-light/50">GET /api/analytics</span>
                <span class="text-[10px] text-emerald-400 bg-emerald-500/10 px-2 py-0.5 rounded">200 OK</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
