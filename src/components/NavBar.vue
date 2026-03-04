<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'
import { animate } from 'motion'

const route = useRoute()
const isScrolled = ref(false)
const mobileOpen = ref(false)
const navEl = ref(null)

const navLinks = [
  { label: 'Services', href: '/#services' },
  { label: 'Work', href: '/#work' },
  { label: 'About', href: '/#about' },
  { label: 'Blog', href: '/blog' },
  { label: 'Contact', href: '/#contact' },
]

function handleScroll() {
  isScrolled.value = window.scrollY > 20
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  if (navEl.value) {
    animate(
      navEl.value,
      { opacity: [0, 1], y: [-12, 0] },
      { duration: 0.6, easing: [0.25, 0.1, 0.25, 1] }
    )
  }
})

onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<template>
  <nav
    ref="navEl"
    style="opacity: 0"
    class="fixed top-0 left-0 right-0 z-50 transition-all duration-300"
    :class="isScrolled ? 'bg-white/90 backdrop-blur-xl py-5' : 'bg-white py-6'"
  >
    <div class="section-inner flex items-center justify-between">
      <!-- Logo (left) -->
      <router-link to="/" class="flex items-center gap-2 no-underline">
        <span class="text-base font-semibold tracking-tight text-dark">ByteLabs()</span>
      </router-link>

      <!-- Right side: links + CTA grouped together -->
      <div class="hidden md:flex items-center gap-9">
        <router-link
          v-for="link in navLinks"
          :key="link.href"
          :to="link.href"
          class="text-[15px] font-medium text-dark/50 hover:text-dark transition-colors"
        >
          {{ link.label }}
        </router-link>
        <router-link to="/#contact" class="btn btn-sm btn-primary">Get in Touch</router-link>
      </div>

      <!-- Mobile toggle -->
      <button
        class="md:hidden w-9 h-9 flex items-center justify-center rounded-lg text-dark cursor-pointer"
        @click="mobileOpen = !mobileOpen"
        aria-label="Toggle menu"
      >
        <svg v-if="!mobileOpen" width="20" height="20" viewBox="0 0 20 20" fill="none">
          <path d="M3 5h14M3 10h14M3 15h14" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
        <svg v-else width="20" height="20" viewBox="0 0 20 20" fill="none">
          <path d="M5 5l10 10M15 5L5 15" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
      </button>
    </div>

    <!-- Separator line (always visible like PointOne) -->
    <div class="nav-line"></div>

    <!-- Mobile menu -->
    <transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div v-if="mobileOpen" class="md:hidden bg-white border-t border-black/5 px-6 py-5">
        <div class="flex flex-col gap-3">
          <router-link
            v-for="link in navLinks"
            :key="link.href"
            :to="link.href"
            class="text-sm font-medium text-dark/60 hover:text-dark py-2"
            @click="mobileOpen = false"
          >
            {{ link.label }}
          </router-link>
          <router-link to="/#contact" class="btn btn-sm btn-primary mt-2" @click="mobileOpen = false">
            Get in Touch
          </router-link>
        </div>
      </div>
    </transition>
  </nav>
</template>
