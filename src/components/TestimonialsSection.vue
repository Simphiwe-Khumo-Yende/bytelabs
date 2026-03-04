<script setup>
import { ref, watch, nextTick, onMounted, onUnmounted } from 'vue'
import { animate, inView } from 'motion'

const cardRef = ref(null)
const quoteRef = ref(null)
const stops = []

const testimonials = [
  {
    quote:
      "ByteLabs turned my vision into a beautifully crafted app. Their attention to detail and understanding of the seasonal rhythms I wanted to convey was exceptional. The team felt like an extension of my own.",
    name: 'Sophie Spiro',
    role: 'Founder — Gaiosophy',
    initials: 'SS',
  },
  {
    quote:
      "Security and reliability were non-negotiable for StrikePoint. ByteLabs delivered a robust platform that our CPOs and clients trust completely. Professional team, solid execution.",
    name: 'Jean Le Roux',
    role: 'CEO — StrikePoint',
    initials: 'JL',
  },
  {
    quote:
      "Building Happay with the ByteLabs team has been incredibly smooth. The code quality and design sensibility they bring is exceptional — they don't just build software, they craft experiences.",
    name: 'Simphiwe Yende',
    role: 'Founder — Happay (ByteLabs Product)',
    initials: 'SY',
  },
]

const current = ref(0)

function next() {
  current.value = (current.value + 1) % testimonials.length
}
function prev() {
  current.value = (current.value - 1 + testimonials.length) % testimonials.length
}

watch(current, async () => {
  await nextTick()
  if (!quoteRef.value) return
  animate(
    quoteRef.value,
    { opacity: [0, 1], y: [12, 0] },
    { duration: 0.45, easing: [0.25, 0.1, 0.25, 1] }
  )
})

onMounted(() => {
  if (cardRef.value) {
    stops.push(
      inView(cardRef.value, ({ target }) => {
        animate(target, { opacity: [0, 1], y: [20, 0], scale: [0.98, 1] }, { duration: 0.7, easing: [0.25, 0.1, 0.25, 1] })
      }, { amount: 0.15 })
    )
  }
})

onUnmounted(() => stops.forEach((s) => s()))
</script>

<template>
  <section class="py-8 md:py-10 bg-light-bg">
    <div class="section-inner">
      <!-- Gradient testimonial card (matching PointOne's purple→gray gradient) -->
      <div
        ref="cardRef"
        style="opacity:0"
        class="relative rounded-2xl overflow-hidden px-8 py-16 md:px-16 md:py-20 min-h-[420px] flex flex-col items-center justify-center"
        :style="{ background: 'linear-gradient(180deg, #7c5da0 0%, #a08aad 40%, #b8b0b8 70%, #c8c4c4 100%)' }"
      >
        <!-- Content -->
        <div class="relative z-10 text-center max-w-3xl mx-auto">
          <!-- Avatar + name -->
          <div class="flex items-center justify-center gap-3 mb-10">
            <div class="w-10 h-10 rounded-full bg-white/20 backdrop-blur-sm flex items-center justify-center">
              <span class="text-sm font-semibold text-white/90">{{ testimonials[current].initials }}</span>
            </div>
            <div class="text-left">
              <div class="text-sm font-semibold text-white/90">{{ testimonials[current].name }}</div>
              <div class="text-xs text-white/50">{{ testimonials[current].role }}</div>
            </div>
          </div>

          <!-- Quote (serif) -->
          <div ref="quoteRef" :key="current">
            <p class="heading-serif text-xl sm:text-2xl md:text-3xl text-white/85 leading-snug mb-10">
              "{{ testimonials[current].quote }}"
            </p>
          </div>
        </div>

        <!-- Nav arrows (sides, like PointOne) -->
        <button
          @click="prev"
          class="absolute left-4 md:left-8 top-1/2 -translate-y-1/2 w-10 h-10 rounded-full bg-white/10 backdrop-blur-sm flex items-center justify-center hover:bg-white/20 transition-colors cursor-pointer z-10"
          aria-label="Previous"
        >
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
            <path d="M15 18l-6-6 6-6" stroke="rgba(255,255,255,0.7)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
        <button
          @click="next"
          class="absolute right-4 md:right-8 top-1/2 -translate-y-1/2 w-10 h-10 rounded-full bg-white/10 backdrop-blur-sm flex items-center justify-center hover:bg-white/20 transition-colors cursor-pointer z-10"
          aria-label="Next"
        >
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
            <path d="M9 18l6-6-6-6" stroke="rgba(255,255,255,0.7)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>

        <!-- Dot indicators (bottom center, like PointOne) -->
        <div class="absolute bottom-6 left-1/2 -translate-x-1/2 flex gap-2 z-10">
          <button
            v-for="(_, idx) in testimonials"
            :key="idx"
            @click="current = idx"
            class="w-2 h-2 rounded-full transition-opacity cursor-pointer"
            :class="idx === current ? 'bg-white/80' : 'bg-white/30'"
            :aria-label="`Go to testimonial ${idx + 1}`"
          />
        </div>
      </div>
    </div>
  </section>
</template>
