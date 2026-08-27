<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate } from 'motion'

const isScrolled = ref(false)
const mobileOpen = ref(false)
const headerEl = ref(null)

const navLinks = [
  { label: 'Services', href: '/#services' },
  { label: 'Work', href: '/#work' },
  { label: 'About', href: '/about' },
  { label: 'Blog', href: '/blog' },
  { label: 'Contact', href: '/contact' },
]

function scrollTo(id) {
  mobileOpen.value = false
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

function onScroll() {
  isScrolled.value = window.scrollY > 50
  if (isScrolled.value) mobileOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
  if (headerEl.value) {
    animate(
      headerEl.value,
      { opacity: [0, 1], y: [-20, 0] },
      { duration: 0.7, easing: [0.25, 0.1, 0.25, 1] }
    )
  }
})

onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<template>
  <header
    ref="headerEl"
    :class="['bl-header', { scrolled: isScrolled, 'menu-open': mobileOpen }]"
    style="opacity: 0"
  >
    <nav class="bl-nav">
      <!-- Logo -->
      <router-link to="/" class="bl-logo">
        ByteLabs()
      </router-link>

      <!-- Desktop links (fade/slide out on scroll) -->
      <ul class="bl-links" :class="{ 'bl-links--hidden': isScrolled }">
        <li v-for="link in navLinks" :key="link.href">
          <router-link :to="link.href">{{ link.label }}</router-link>
        </li>
      </ul>

      <!-- CTA button (hides on scroll) -->
      <div class="bl-nav-actions" :class="{ 'bl-nav-actions--hidden': isScrolled }">
        <router-link to="/contact" class="bl-cta-btn">Get in Touch</router-link>
      </div>

      <!-- Mobile hamburger (hides on scroll) -->
      <button
        class="bl-mobile-btn"
        :class="{ 'bl-mobile-btn--hidden': isScrolled }"
        @click="mobileOpen = !mobileOpen"
        aria-label="Toggle menu"
      >
        <span></span><span></span><span></span>
      </button>
    </nav>

    <!-- Mobile menu -->
    <div v-if="mobileOpen" class="bl-mobile-menu">
      <router-link
        v-for="link in navLinks"
        :key="link.href"
        :to="link.href"
        @click="mobileOpen = false"
      >
        {{ link.label }}
      </router-link>
    </div>
  </header>
</template>

<style scoped>
/* ── Floating glassmorphism header ── */
.bl-header {
  position: fixed;
  top: 1rem;
  left: 0;
  right: 0;
  margin-left: auto;
  margin-right: auto;
  z-index: 100;
  width: calc(100% - 2rem);
  max-width: 1112px;
  display: flex;
  flex-direction: column;
  background: rgba(255, 255, 255, 0.55);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.08);
  border-radius: 9999px;
  border: 1px solid rgba(255, 255, 255, 0.35);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  padding: 0 2rem;
  transition:
    width 0.5s cubic-bezier(0.4, 0, 0.2, 1),
    max-width 0.5s cubic-bezier(0.4, 0, 0.2, 1),
    border-radius 0.4s cubic-bezier(0.4, 0, 0.2, 1),
    background 0.4s,
    box-shadow 0.4s,
    border-color 0.4s;
}

.bl-header.scrolled {
  width: 280px;
  max-width: 90vw;
  background: rgba(255, 255, 255, 0.65);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
  border-color: rgba(255, 255, 255, 0.4);
  border-radius: 2rem;
}

.bl-header.menu-open {
  border-radius: 1.5rem;
}

/* ── Nav layout ── */
.bl-nav {
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 64px;
  flex-shrink: 0;
}

/* ── Logo ── */
.bl-logo {
  display: flex;
  align-items: center;
  font-weight: 600;
  font-size: 1rem;
  text-decoration: none;
  color: var(--color-dark);
  white-space: nowrap;
  letter-spacing: -0.01em;
  transition: font-size 0.4s;
}

.bl-header.scrolled .bl-logo {
  font-size: 0.95rem;
}

/* ── Desktop links ── */
.bl-links {
  display: flex;
  gap: 2rem;
  list-style: none;
  max-width: 600px;
  overflow: hidden;
  opacity: 1;
  transform: translateY(0);
  pointer-events: auto;
  transition:
    max-width 0.5s cubic-bezier(0.4, 0, 0.2, 1),
    opacity 0.4s,
    gap 0.5s,
    transform 0.4s;
}

.bl-links--hidden {
  max-width: 0;
  opacity: 0;
  gap: 0;
  pointer-events: none;
  transform: translateY(-16px);
}

.bl-links a {
  text-decoration: none;
  color: var(--color-dark);
  opacity: 0.45;
  font-size: 0.9rem;
  font-weight: 500;
  white-space: nowrap;
  position: relative;
  transition: opacity 0.3s;
}

.bl-links a::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 1.5px;
  background: var(--color-dark);
  transition: width 0.3s;
}

.bl-links a:hover {
  opacity: 1;
}

.bl-links a:hover::after {
  width: 100%;
}

/* ── CTA button ── */
.bl-nav-actions {
  overflow: hidden;
  max-width: 200px;
  opacity: 1;
  transition:
    max-width 0.5s cubic-bezier(0.4, 0, 0.2, 1),
    opacity 0.4s;
}

.bl-nav-actions--hidden {
  max-width: 0;
  opacity: 0;
  pointer-events: none;
}

.bl-cta-btn {
  display: inline-flex;
  align-items: center;
  padding: 0.55rem 1.4rem;
  background: var(--color-dark);
  color: #fff;
  border: none;
  border-radius: 50px;
  font-weight: 500;
  font-size: 0.85rem;
  text-decoration: none;
  white-space: nowrap;
  transition: opacity 0.2s, transform 0.2s;
}

.bl-cta-btn:hover {
  opacity: 0.85;
  transform: scale(1.02);
}

/* ── Mobile hamburger ── */
.bl-mobile-btn {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 5px;
  transition: max-width 0.5s ease, opacity 0.3s ease;
  overflow: hidden;
}

.bl-mobile-btn--hidden {
  max-width: 0;
  opacity: 0;
  pointer-events: none;
  padding: 0;
}

.bl-mobile-btn span {
  width: 22px;
  height: 2px;
  background: var(--color-dark);
  border-radius: 2px;
}

/* ── Mobile menu ── */
.bl-mobile-menu {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  padding: 0.5rem 1.5rem 1rem;
  border-top: 1px solid rgba(24, 26, 28, 0.06);
}

.bl-mobile-menu a {
  text-decoration: none;
  color: var(--color-dark);
  opacity: 0.6;
  font-size: 0.9rem;
  font-weight: 500;
  padding: 0.5rem 0;
  transition: opacity 0.2s;
}

.bl-mobile-menu a:hover {
  opacity: 1;
}

/* ── Responsive ── */
@media (max-width: 768px) {
  .bl-header {
    width: calc(100% - 2rem);
    border-radius: 1.5rem;
  }

  .bl-header:has(.bl-mobile-menu) {
    border-radius: 1.5rem;
  }

  .bl-links,
  .bl-nav-actions {
    display: none;
  }

  .bl-mobile-btn {
    display: flex;
  }
}
</style>
