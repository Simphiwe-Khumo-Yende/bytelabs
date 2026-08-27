<script setup>
import { ref, onMounted } from 'vue'
import { animate, stagger, inView } from 'motion'
import { Badge } from '@/components/ui/badge'
import { Card, CardContent, CardHeader, CardTitle, CardDescription } from '@/components/ui/card'
import { Avatar, AvatarFallback } from '@/components/ui/avatar'
import { Separator } from '@/components/ui/separator'
import { HoverCard, HoverCardContent, HoverCardTrigger } from '@/components/ui/hover-card'

const pageRef = ref(null)

const companyFacts = [
  { label: 'Registered', value: '14 Oct 2025' },
  { label: 'Reg. number', value: '2025/807699/07' },
  { label: 'Type', value: 'Private Company' },
  { label: 'Status', value: 'In Business' },
  { label: 'Location', value: 'Pretoria, South Africa' },
  { label: 'Financial year end', value: 'February' },
]

const skills = [
  { name: 'Vue.js', category: 'Frontend' },
  { name: 'Flutter', category: 'Mobile' },
  { name: 'Python', category: 'Backend' },
  { name: 'Django REST', category: 'Backend' },
  { name: 'Dart', category: 'Mobile' },
  { name: 'JavaScript', category: 'Frontend' },
  { name: 'PostgreSQL', category: 'Database' },
  { name: 'AWS S3', category: 'Cloud' },
  { name: 'Tailwind CSS', category: 'Frontend' },
  { name: 'Celery / Redis', category: 'Backend' },
  { name: 'Git & CI/CD', category: 'DevOps' },
  { name: 'API Architecture', category: 'Backend' },
]

const timeline = [
  {
    year: '2025 — present',
    role: 'Software Engineer',
    company: 'The Good People Data Company',
    note: 'Building large-scale KYC, KYB & compliance verification platforms.',
  },
  {
    year: '2025 — 2026',
    role: 'Founding Engineer',
    company: 'Gaiosophy',
    note: 'Sole engineer, concept to production — cross-platform mobile app.',
  },
  {
    year: '2025',
    role: 'Founded ByteLabs (Pty) Ltd',
    company: 'Reg. 2025/807699/07',
    note: 'Officially registered to deliver custom software across web & mobile.',
  },
  {
    year: 'Jan 2025',
    role: 'Software Engineer Intern',
    company: 'Empire Partner Foundation',
    note: 'Contributed to the TGPDC verification platform before IP handover.',
  },
  {
    year: '2023 — 2024',
    role: 'NQF 5 · Systems Development',
    company: 'WeThinkCode',
    note: 'Graduated 2nd Semester Top 50.',
  },
]

const values = [
  {
    title: 'Quality First',
    body: 'Every line is tested and built to last. No shortcuts, no cut corners.',
    icon: '◆',
  },
  {
    title: 'Transparent Process',
    body: 'Weekly updates, clear timelines, no surprises. You always know where things stand.',
    icon: '◇',
  },
  {
    title: 'Long-term Partnership',
    body: 'The relationship doesn\'t end at launch. ByteLabs grows with your product.',
    icon: '○',
  },
]

onMounted(() => {
  if (!pageRef.value) return
  inView(
    pageRef.value,
    () => {
      animate(
        pageRef.value.querySelectorAll('[data-a]'),
        { opacity: [0, 1], y: [28, 0] },
        { duration: 0.6, delay: stagger(0.08), easing: [0.25, 0.1, 0.25, 1] }
      )
    },
    { amount: 0.05 }
  )
})
</script>

<template>
  <div ref="pageRef" class="about-page">

    <!-- ── Hero ── -->
    <section class="about-hero">
      <div class="about-inner">
        <div data-a style="opacity:0" class="about-hero-pill">
          <Badge variant="outline" class="tracking-widest text-[11px] uppercase">About ByteLabs</Badge>
        </div>
        <h1 data-a style="opacity:0" class="about-hero-heading">
          We build software<br>that ships.
        </h1>
        <p data-a style="opacity:0" class="about-hero-sub">
          ByteLabs is a registered South African software studio that designs and builds
          custom web apps, mobile apps, and backend systems. From product discovery
          through architecture, design, and deployment — we own the full delivery.
        </p>
      </div>
    </section>

    <!-- ── What we do ── -->
    <section class="about-section">
      <div class="about-inner">
        <div data-a style="opacity:0" class="about-section-label">
          <Badge variant="outline" class="tracking-widest text-[11px] uppercase">What We Do</Badge>
        </div>
        <h2 data-a style="opacity:0" class="about-section-heading">One studio. Every layer.</h2>

        <div data-a style="opacity:0" class="what-grid">
          <Card class="what-card">
            <CardHeader class="pb-2">
              <CardTitle class="text-base">Web Applications</CardTitle>
            </CardHeader>
            <CardContent>
              <p class="text-sm text-muted-foreground leading-relaxed">
                Performant, scalable web apps built with Vue.js, Tailwind CSS and REST or
                GraphQL backends. From landing pages to complex multi-tenant SaaS platforms.
              </p>
            </CardContent>
          </Card>
          <Card class="what-card">
            <CardHeader class="pb-2">
              <CardTitle class="text-base">Mobile Apps</CardTitle>
            </CardHeader>
            <CardContent>
              <p class="text-sm text-muted-foreground leading-relaxed">
                Cross-platform iOS &amp; Android apps with Flutter &amp; Dart. Single codebase,
                native feel. Built for real users — not just demo screens.
              </p>
            </CardContent>
          </Card>
          <Card class="what-card">
            <CardHeader class="pb-2">
              <CardTitle class="text-base">Backend &amp; APIs</CardTitle>
            </CardHeader>
            <CardContent>
              <p class="text-sm text-muted-foreground leading-relaxed">
                Django REST APIs, PostgreSQL databases, Celery task queues, AWS S3 storage,
                and CI/CD pipelines. Production-grade from day one.
              </p>
            </CardContent>
          </Card>
        </div>
      </div>
    </section>

    <!-- ── Company facts ── -->
    <section class="about-section about-section--alt">
      <div class="about-inner">
        <div data-a style="opacity:0" class="about-section-label">
          <Badge variant="outline" class="tracking-widest text-[11px] uppercase">Company</Badge>
        </div>
        <h2 data-a style="opacity:0" class="about-section-heading">ByteLabs (Pty) Ltd</h2>
        <p data-a style="opacity:0" class="about-section-sub">
          Incorporated in South Africa under the Companies Act, 2008.
          Operating as a registered private company and trusted by growing startups.
        </p>

        <div data-a style="opacity:0" class="facts-grid">
          <div v-for="fact in companyFacts" :key="fact.label" class="fact-item">
            <span class="fact-label">{{ fact.label }}</span>
            <span class="fact-value">{{ fact.value }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ── Founder card ── -->
    <section class="about-section">
      <div class="about-inner">
        <div data-a style="opacity:0" class="about-section-label">
          <Badge variant="outline" class="tracking-widest text-[11px] uppercase">The Founder</Badge>
        </div>
        <h2 data-a style="opacity:0" class="about-section-heading">One engineer. End-to-end.</h2>
        <p data-a style="opacity:0" class="about-section-sub">
          Running lean means every project gets undivided attention. No handoffs, no context lost in translation.
        </p>
        <div data-a style="opacity:0">
          <Card class="founder-card">
            <CardContent class="founder-body">
              <!-- Avatar + identity -->
              <div class="founder-identity">
                <Avatar class="founder-avatar">
                  <AvatarFallback class="founder-avatar-fb">SY</AvatarFallback>
                </Avatar>
                <div>
                  <p class="founder-name">Simphiwe Yende</p>
                  <p class="founder-role">Founder &amp; Lead Developer</p>
                  <div class="founder-links">
                    <a href="https://linkedin.com/in/simphiwe-khumo" target="_blank" rel="noopener" class="founder-link">
                      LinkedIn ↗
                    </a>
                    <span class="founder-link-sep">·</span>
                    <a href="mailto:siphiweyende371@gmail.com" class="founder-link">
                      siphiweyende371@gmail.com
                    </a>
                    <span class="founder-link-sep">·</span>
                    <span class="founder-link">Pretoria, South Africa</span>
                  </div>
                </div>
              </div>

              <Separator class="my-6" />

              <!-- Bio -->
              <div class="founder-bio">
                <p>
                  I'm a full-stack software engineer with a focus on clean architecture and polished interfaces.
                  I specialise in Vue.js and Flutter on the frontend, Django REST on the backend, and I'm comfortable
                  owning the entire stack — from system design to cloud deployment.
                </p>
                <p class="mt-4">
                  After building a large-scale KYC/KYB verification platform at The Good People Data Company and
                  taking Gaiosophy from zero to production as their sole engineer, I founded ByteLabs to channel that
                  experience into client products — startups, scaleups, and internal tools.
                </p>
                <p class="mt-4">
                  Running lean means every project gets my full attention. No handoffs to junior developers, no
                  context lost in translation.
                </p>
              </div>
            </CardContent>
          </Card>
        </div>
      </div>
    </section>

    <!-- ── Skills ── -->
    <section class="about-section about-section--alt">
      <div class="about-inner">
        <div data-a style="opacity:0" class="about-section-label">
          <Badge variant="outline" class="tracking-widest text-[11px] uppercase">Skills &amp; Stack</Badge>
        </div>
        <h2 data-a style="opacity:0" class="about-section-heading">Built across the full stack.</h2>

        <div data-a style="opacity:0" class="skills-grid">
          <HoverCard v-for="skill in skills" :key="skill.name" :open-delay="100">
            <HoverCardTrigger as-child>
              <div class="skill-chip">
                <span class="skill-name">{{ skill.name }}</span>
                <span class="skill-cat">{{ skill.category }}</span>
              </div>
            </HoverCardTrigger>
            <HoverCardContent class="w-auto px-3 py-2 text-xs text-muted-foreground">
              {{ skill.category }}
            </HoverCardContent>
          </HoverCard>
        </div>
      </div>
    </section>

    <!-- ── Timeline ── -->
    <section class="about-section">
      <div class="about-inner">
        <div data-a style="opacity:0" class="about-section-label">
          <Badge variant="outline" class="tracking-widest text-[11px] uppercase">Experience</Badge>
        </div>
        <h2 data-a style="opacity:0" class="about-section-heading">Where I've been.</h2>

        <div class="timeline">
          <div v-for="(item, i) in timeline" :key="i" data-a style="opacity:0" class="timeline-row">
            <div class="timeline-year">{{ item.year }}</div>
            <div class="timeline-dot-col">
              <div class="timeline-dot"></div>
              <div v-if="i < timeline.length - 1" class="timeline-line"></div>
            </div>
            <Card class="timeline-card">
              <CardHeader class="pb-1 pt-4 px-5">
                <span class="timeline-year-inline">{{ item.year }}</span>
                <CardTitle class="text-sm font-semibold leading-tight">{{ item.role }}</CardTitle>
                <CardDescription class="text-xs">{{ item.company }}</CardDescription>
              </CardHeader>
              <CardContent class="pb-4 px-5 pt-0">
                <p class="text-sm text-muted-foreground leading-relaxed">{{ item.note }}</p>
              </CardContent>
            </Card>
          </div>
        </div>
      </div>
    </section>

    <!-- ── Values ── -->
    <section class="about-section about-section--alt">
      <div class="about-inner">
        <div data-a style="opacity:0" class="about-section-label">
          <Badge variant="outline" class="tracking-widest text-[11px] uppercase">How I Work</Badge>
        </div>
        <h2 data-a style="opacity:0" class="about-section-heading">Principles, not promises.</h2>

        <div class="values-grid">
          <Card v-for="v in values" :key="v.title" data-a style="opacity:0" class="value-card">
            <CardHeader class="pb-2">
              <span class="value-icon">{{ v.icon }}</span>
              <CardTitle class="text-base mt-3">{{ v.title }}</CardTitle>
            </CardHeader>
            <CardContent>
              <p class="text-sm text-muted-foreground leading-relaxed">{{ v.body }}</p>
            </CardContent>
          </Card>
        </div>
      </div>
    </section>

    <!-- ── CTA ── -->
    <section class="about-section about-cta">
      <div class="about-inner text-center">
        <h2 data-a style="opacity:0" class="about-cta-heading">Have something to build?</h2>
        <p data-a style="opacity:0" class="about-cta-sub">
          I take on a small number of projects at a time so I can deliver properly.
          Reach out early.
        </p>
        <div data-a style="opacity:0">
          <router-link to="/contact" class="about-cta-btn">Start a Project</router-link>
        </div>
      </div>
    </section>

  </div>
</template>

<style scoped>
.about-page {
  background: #fff;
  min-height: 100vh;
}

.about-inner {
  max-width: 820px;
  margin: 0 auto;
  padding: 0 24px;
}

/* ── Hero ── */
.about-hero {
  padding: 120px 0 80px;
  border-bottom: 1px solid rgba(24, 26, 28, 0.06);
}

.about-hero-pill {
  margin-bottom: 28px;
}

.about-hero-heading {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(3rem, 7vw, 5rem);
  font-weight: 400;
  line-height: 1.05;
  letter-spacing: -0.02em;
  color: #181a1c;
  margin-bottom: 28px;
}

.about-hero-sub {
  font-size: 17px;
  color: rgba(24, 26, 28, 0.55);
  line-height: 1.7;
  max-width: 560px;
}

/* ── Sections ── */
.about-section {
  padding: 80px 0;
  border-bottom: 1px solid rgba(24, 26, 28, 0.06);
}

.about-section--alt {
  background: #fafafa;
}

.about-section-label {
  margin-bottom: 20px;
}

.about-section-heading {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(1.8rem, 4vw, 2.8rem);
  font-weight: 400;
  letter-spacing: -0.02em;
  color: #181a1c;
  margin-bottom: 40px;
  line-height: 1.1;
}

/* ── What we do ── */
.what-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}

.what-card {
  border: 1px solid rgba(24, 26, 28, 0.07);
  background: #fff;
}

/* ── Company facts ── */
.about-section-sub {
  font-size: 15px;
  color: rgba(24, 26, 28, 0.55);
  line-height: 1.7;
  margin-top: -20px;
  margin-bottom: 40px;
}

.facts-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: rgba(24, 26, 28, 0.07);
  border: 1px solid rgba(24, 26, 28, 0.07);
  border-radius: 14px;
  overflow: hidden;
}

.fact-item {
  background: #fff;
  padding: 20px 24px;
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.fact-label {
  font-size: 11px;
  font-weight: 500;
  color: rgba(24, 26, 28, 0.4);
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

.fact-value {
  font-size: 14px;
  font-weight: 600;
  color: #181a1c;
}

/* ── Founder card ── */
.founder-card {
  border: 1px solid rgba(24, 26, 28, 0.08);
  box-shadow: 0 4px 24px -4px rgba(24, 26, 28, 0.07);
}

.founder-body {
  padding: 32px;
}

.founder-identity {
  display: flex;
  align-items: flex-start;
  gap: 20px;
}

.founder-avatar {
  width: 64px;
  height: 64px;
  flex-shrink: 0;
}

.founder-avatar-fb {
  background: linear-gradient(135deg, #42b883 0%, #35495e 100%);
  color: #fff;
  font-size: 18px;
  font-weight: 600;
}

.founder-name {
  font-size: 18px;
  font-weight: 700;
  color: #181a1c;
  line-height: 1.2;
}

.founder-role {
  font-size: 13px;
  color: rgba(24, 26, 28, 0.5);
  margin-top: 2px;
  margin-bottom: 10px;
}

.founder-links {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 6px;
  font-size: 12px;
}

.founder-link {
  color: rgba(24, 26, 28, 0.55);
  text-decoration: none;
  transition: color 0.15s;
}

.founder-link:hover {
  color: #181a1c;
}

a.founder-link {
  text-decoration: underline;
  text-underline-offset: 3px;
}

.founder-link-sep {
  color: rgba(24, 26, 28, 0.25);
}

.founder-bio p {
  font-size: 15px;
  line-height: 1.75;
  color: rgba(24, 26, 28, 0.7);
}

/* ── Skills ── */
.skills-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.skill-chip {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  border-radius: 50px;
  border: 1px solid rgba(24, 26, 28, 0.1);
  background: #fff;
  cursor: default;
  transition: border-color 0.15s, box-shadow 0.15s;
}

.skill-chip:hover {
  border-color: rgba(24, 26, 28, 0.3);
  box-shadow: 0 2px 8px rgba(24, 26, 28, 0.06);
}

.skill-name {
  font-size: 13px;
  font-weight: 500;
  color: #181a1c;
}

.skill-cat {
  font-size: 11px;
  color: rgba(24, 26, 28, 0.4);
}

/* ── Timeline ── */
.timeline {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.timeline-row {
  display: grid;
  grid-template-columns: 140px 28px 1fr;
  gap: 0 16px;
  align-items: start;
}

.timeline-year {
  font-size: 12px;
  font-weight: 500;
  color: rgba(24, 26, 28, 0.4);
  padding-top: 18px;
  text-align: right;
  white-space: nowrap;
}

.timeline-dot-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 20px;
}

.timeline-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #181a1c;
  flex-shrink: 0;
}

.timeline-line {
  width: 1px;
  flex: 1;
  min-height: 24px;
  background: rgba(24, 26, 28, 0.12);
  margin-top: 4px;
  margin-bottom: 4px;
}

.timeline-card {
  margin-bottom: 16px;
  border: 1px solid rgba(24, 26, 28, 0.07);
  box-shadow: none;
}

/* hidden on desktop; shown inside the card on mobile */
.timeline-year-inline {
  display: none;
  font-size: 11px;
  font-weight: 500;
  color: rgba(24, 26, 28, 0.4);
  margin-bottom: 4px;
}

/* ── Values ── */
.values-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}

.value-card {
  border: 1px solid rgba(24, 26, 28, 0.07);
  background: #fff;
}

.value-icon {
  font-size: 18px;
  color: rgba(24, 26, 28, 0.35);
}

/* ── CTA ── */
.about-cta {
  border-bottom: none;
  padding: 100px 0;
}

.about-cta-heading {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2rem, 5vw, 3.5rem);
  font-weight: 400;
  letter-spacing: -0.02em;
  color: #181a1c;
  margin-bottom: 20px;
}

.about-cta-sub {
  font-size: 16px;
  color: rgba(24, 26, 28, 0.5);
  margin-bottom: 40px;
  max-width: 420px;
  margin-left: auto;
  margin-right: auto;
  line-height: 1.65;
}

.about-cta-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 13px 32px;
  background: #181a1c;
  color: #fff;
  font-size: 14px;
  font-weight: 500;
  border-radius: 50px;
  text-decoration: none;
  transition: opacity 0.2s;
}

.about-cta-btn:hover {
  opacity: 0.85;
}

/* ── Mobile ── */
@media (max-width: 640px) {
  .about-hero {
    padding: 100px 0 60px;
  }

  .about-section {
    padding: 60px 0;
  }

  .founder-body {
    padding: 24px;
  }

  .founder-identity {
    flex-direction: column;
    gap: 14px;
  }

  .timeline-row {
    grid-template-columns: 24px 1fr;
  }

  /* desktop year label hidden; inline label inside card takes over */
  .timeline-year {
    display: none;
  }

  /* dot col shifts to col 1, card to col 2 */
  .timeline-dot-col {
    grid-column: 1;
  }

  .timeline-card {
    grid-column: 2;
  }

  .timeline-year-inline {
    display: block;
  }

  .what-grid {
    grid-template-columns: 1fr;
  }

  .facts-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .values-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 900px) {
  .what-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .facts-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .values-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
