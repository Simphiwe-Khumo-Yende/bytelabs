<script setup>
import HeroSection from '../components/HeroSection.vue'
import StatsSection from '../components/StatsSection.vue'
import ServicesSection from '../components/ServicesSection.vue'
import DesignSection from '../components/DesignSection.vue'
import ProcessSection from '../components/ProcessSection.vue'
import TeamSection from '../components/TeamSection.vue'
import FAQSection from '../components/FAQSection.vue'
import CtaSection from '../components/CtaSection.vue'
</script>

<template>
  <main>
    <!-- 1. Hook: what we do + social proof -->
    <HeroSection />
    <StatsSection />

    <!-- 2. Convince: our capabilities -->
    <ServicesSection />
    <DesignSection />
    <ProcessSection />

    <!-- 4. Connect: who we are -->
    <TeamSection />

    <!-- 5. Close: remove objections + CTA -->
    <FAQSection />
    <CtaSection />
  </main>
</template>
