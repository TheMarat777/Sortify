<template>
  <main class="oi">
    <div class="oi__container">

      <!-- ───── Hero ───── -->
      <section class="oi__hero">
        <span class="oi__badge">Environmental Impact</span>
        <h1 class="oi__title">Our Impact</h1>
        <p class="oi__subtitle">
          Measuring real environmental outcomes — every kilogram diverted from
          landfill, every tonne of CO₂ avoided, and every material given a second
          life through the Sortify platform in Denmark.
        </p>
      </section>

      <!-- ───── Headline Stats (full-bleed) ───── -->
      <section class="oi__headline-section">
        <h2 class="oi__section-title">
          <span class="oi__section-icon"></span>
          Impact at a Glance
        </h2>
        <div class="oi__headline-grid">
          <div v-for="h in headlines" :key="h.label" class="oi__headline-card" :style="{ '--hl-color': h.color }">
            <span class="oi__headline-value">{{ h.value }}</span>
            <span class="oi__headline-label">{{ h.label }}</span>
            <p class="oi__headline-desc">{{ h.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── Material Recovery ───── -->
      <section class="oi__recovery">
        <h2 class="oi__section-title">
          <span class="oi__section-icon"></span>
          Materials Recovered by Type
        </h2>
        <p class="oi__section-desc">
          Breakdown of all materials registered, matched and reused through
          the Sortify marketplace and project dashboards.
        </p>
        <div class="oi__recovery-grid">
          <div v-for="m in materialStats" :key="m.name" class="oi__recovery-card" :style="{ '--mat-color': m.color }">
            <h3 class="oi__recovery-name">{{ m.name }}</h3>
            <span class="oi__recovery-amount">{{ m.amount }}</span>
            <div class="oi__recovery-bar">
              <div class="oi__recovery-fill" :style="{ width: m.pct }" />
            </div>
            <span class="oi__recovery-pct">{{ m.pct }} of total</span>
          </div>
        </div>
      </section>

      <!-- ───── Environmental Savings (full-bleed) ───── -->
      <section class="oi__savings-section">
        <h2 class="oi__section-title">
          <span class="oi__section-icon"></span>
          Environmental Savings
        </h2>
        <p class="oi__section-desc">
          Every reused material avoids the environmental cost of producing
          a new one — from mining raw resources to manufacturing and transport.
        </p>
        <div class="oi__savings-grid">
          <div v-for="s in savings" :key="s.title" class="oi__saving-card">
            <div>
              <h3 class="oi__saving-title">{{ s.title }}</h3>
              <span class="oi__saving-value">{{ s.value }}</span>
              <p class="oi__saving-desc">{{ s.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Project Highlights ───── -->
      <section class="oi__projects">
        <h2 class="oi__section-title">
          <span class="oi__section-icon"></span>
          Project Highlights
        </h2>
        <p class="oi__section-desc">
          Real demolition projects across Denmark demonstrating the power of
          material recovery and circular construction.
        </p>
        <div class="oi__projects-grid">
          <div v-for="p in projects" :key="p.title" class="oi__project-card">
            <div class="oi__project-badge">{{ p.region }}</div>
            <h3 class="oi__project-title">{{ p.title }}</h3>
            <p class="oi__project-desc">{{ p.desc }}</p>
            <div class="oi__project-stats">
              <div v-for="st in p.stats" :key="st.label" class="oi__project-stat">
                <span class="oi__project-stat-value">{{ st.value }}</span>
                <span class="oi__project-stat-label">{{ st.label }}</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Goals & Targets (full-bleed) ───── -->
      <section class="oi__goals-section">
        <h2 class="oi__section-title">
          <span class="oi__section-icon"></span>
          2026 Goals
        </h2>
        <div class="oi__goals-grid">
          <div v-for="g in goals" :key="g.title" class="oi__goal-card" :style="{ '--goal-color': g.color }">
            <div class="oi__goal-progress-ring">
              <svg viewBox="0 0 60 60">
                <circle cx="30" cy="30" r="26" fill="none" stroke="#eee" stroke-width="4" />
                <circle
                  cx="30" cy="30" r="26" fill="none"
                  :stroke="g.color" stroke-width="4"
                  stroke-linecap="round"
                  :stroke-dasharray="163.36"
                  :stroke-dashoffset="163.36 - (163.36 * g.progress / 100)"
                  transform="rotate(-90 30 30)"
                />
              </svg>
              <span class="oi__goal-pct">{{ g.progress }}%</span>
            </div>
            <div>
              <h3 class="oi__goal-title">{{ g.title }}</h3>
              <p class="oi__goal-desc">{{ g.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── How You Can Help ───── -->
      <section class="oi__help">
        <h2 class="oi__section-title">
          <span class="oi__section-icon"></span>
          How You Can Help
        </h2>
        <div class="oi__help-grid">
          <div v-for="h in helpItems" :key="h.title" class="oi__help-card" :style="{ '--help-accent': h.color }">
            <h3 class="oi__help-title">{{ h.title }}</h3>
            <p class="oi__help-desc">{{ h.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── CTA Banner ───── -->
      <section class="oi__cta-banner">
        <div class="oi__cta-inner">
          <h2 class="oi__cta-title">Be part of the impact</h2>
          <p class="oi__cta-desc">
            Every material you register, buy or reuse adds to our collective
            environmental savings. Join the movement today.
          </p>
          <div class="oi__cta-actions">
            <NuxtLink to="/marketplace" class="oi__cta-btn oi__cta-btn--primary">
              Browse Marketplace →
            </NuxtLink>
            <NuxtLink to="/dashboard" class="oi__cta-btn oi__cta-btn--secondary">
              View Projects
            </NuxtLink>
          </div>
        </div>
      </section>

    </div>
  </main>
</template>

<script setup lang="ts">
const headlines = [
  { value: '92,240 kg', label: 'Materials Registered', color: '#2f7a3e', desc: 'Total weight of construction materials logged on the platform.' },
  { value: '38 t', label: 'CO₂ Saved (est.)', color: '#0e7490', desc: 'Estimated greenhouse gas emissions avoided through material reuse.' },
  { value: '6', label: 'Active Projects', color: '#b45309', desc: 'Demolition projects currently tracked across Denmark.' },
  { value: '74', label: 'Materials Listed', color: '#7c3aed', desc: 'Individual material listings available on the marketplace.' },
  { value: '61%', label: 'Average Reuse Rate', color: '#16a34a', desc: 'Percentage of registered materials that found a second life.' },
  { value: '12', label: 'Municipalities Covered', color: '#6b4f32', desc: 'Danish municipalities with at least one active project on Sortify.' },
]

const materialStats = [
  { name: 'Concrete & Masonry', amount: '41,500 kg', pct: '45%', color: '#6b7280' },
  { name: 'Timber & Wood', amount: '18,450 kg', pct: '20%', color: '#92400e' },
  { name: 'Structural Steel', amount: '11,070 kg', pct: '12%', color: '#374151' },
  { name: 'Bricks', amount: '9,224 kg', pct: '10%', color: '#b45309' },
  { name: 'Windows & Glass', amount: '5,534 kg', pct: '6%', color: '#0e7490' },
  { name: 'Other Materials', amount: '6,462 kg', pct: '7%', color: '#7c3aed' },
]

const savings = [
  { title: 'Avoided Manufacturing', value: '38 tonnes CO₂', desc: 'Reusing steel, concrete and timber avoids the energy-intensive process of manufacturing new materials from raw resources.' },
  { title: 'Reduced Transport', value: '12,400 km saved', desc: 'Local material redistribution through Sortify cuts long-distance transport of new materials from factories and quarries.' },
  { title: 'Landfill Diversion', value: '56.3 tonnes diverted', desc: 'Materials that would have ended up in Danish landfills are instead sorted, graded and redirected to new construction projects.' },
  { title: 'Water Conservation', value: '420,000 litres', desc: 'Avoiding new concrete and steel production conserves the enormous water volumes used in mining, processing and manufacturing.' },
  { title: 'Raw Resource Savings', value: '68 tonnes', desc: 'Every reused beam, brick and window pane reduces demand for virgin sand, ore, timber and aggregate extraction.' },
  { title: 'Energy Saved', value: '185 MWh', desc: 'The embodied energy preserved by reusing materials instead of producing new ones — enough to power 45 homes for a year.' },
]

const projects = [
  {
    region: 'Aarhus',
    title: 'Aarhus University Hospital',
    desc: 'Major demolition of the old hospital wing — one of the largest selective demolition projects in Jutland with exceptional recovery rates.',
    stats: [
      { value: '32,400 kg', label: 'Registered' },
      { value: '78%', label: 'Reuse Rate' },
      { value: '14 t CO₂', label: 'Saved' },
    ],
  },
  {
    region: 'Copenhagen',
    title: 'Carlsberg Brewery Warehouse',
    desc: 'Heritage transformation project preserving original industrial materials — brickwork, steel trusses and hardwood flooring redistributed across Denmark.',
    stats: [
      { value: '18,200 kg', label: 'Registered' },
      { value: '91%', label: 'Reuse Rate' },
      { value: '8 t CO₂', label: 'Saved' },
    ],
  },
  {
    region: 'Odense',
    title: 'Odense Industrial Silo',
    desc: 'Concrete-heavy demolition showcasing how crushed concrete aggregate can replace virgin materials in road and foundation work.',
    stats: [
      { value: '21,800 kg', label: 'Registered' },
      { value: '52%', label: 'Reuse Rate' },
      { value: '9 t CO₂', label: 'Saved' },
    ],
  },
  {
    region: 'Aalborg',
    title: 'Aalborg Cement Factory',
    desc: 'The largest project on Sortify — massive industrial structures yielding thousands of tonnes of steel and reinforced concrete.',
    stats: [
      { value: '54,000 kg', label: 'Registered' },
      { value: '76%', label: 'Reuse Rate' },
      { value: '22 t CO₂', label: 'Saved' },
    ],
  },
]

const goals = [
  { title: '150 tonnes registered', desc: 'Scale platform registrations to 150,000 kg of construction materials by end of 2026.', progress: 62, color: '#2f7a3e' },
  { title: '15 active projects', desc: 'Expand from 6 to 15 tracked demolition projects across all five Danish regions.', progress: 40, color: '#0e7490' },
  { title: '75% reuse rate', desc: 'Increase average material reuse rate from 61% to 75% through better matching and quality grading.', progress: 81, color: '#b45309' },
  { title: '100 t CO₂ avoided', desc: 'Reach a cumulative 100 tonnes of estimated CO₂ savings through material reuse.', progress: 38, color: '#7c3aed' },
  { title: '25 municipalities', desc: 'Double our geographic coverage to 25 Danish municipalities with active listings.', progress: 48, color: '#16a34a' },
  { title: '200 marketplace listings', desc: 'Grow the marketplace from 74 to 200 active material listings for buyers to browse.', progress: 37, color: '#6b4f32' },
]

const helpItems = [
  { title: 'Demolition Contractors', color: '#2f7a3e', desc: 'Register salvaged materials from your demolition sites. The sooner materials are listed, the more likely they find a buyer.' },
  { title: 'Builders & Architects', color: '#0e7490', desc: 'Browse the marketplace for quality reclaimed materials. Save money and reduce the carbon footprint of your projects.' },
  { title: 'Municipalities', color: '#b45309', desc: 'Use Sortify to track waste management across your construction projects and report on circular economy targets.' },
  { title: 'Researchers & Students', color: '#7c3aed', desc: 'Access real data on material flows, recovery rates and environmental impact to support circular construction research.' },
]
</script>

<style scoped>
.oi {
  flex: 1;
  padding: 40px 24px 0;
  background: linear-gradient(175deg, #f6f7f3 0%, #eef0e8 100%);
}
.oi__container {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 56px;
}
.oi__container > :last-child {
  margin-bottom: -56px;
}

/* ──── Hero ──── */
.oi__hero { max-width: 680px; }
.oi__badge {
  display: inline-block;
  background: rgba(47,122,62,0.1);
  color: var(--color-green, #2f7a3e);
  font-size: 0.82rem;
  font-weight: 700;
  padding: 4px 14px;
  border-radius: 20px;
  margin-bottom: 10px;
}
.oi__title {
  font-size: 2.2rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0;
  letter-spacing: -0.02em;
}
.oi__subtitle {
  margin: 10px 0 0;
  font-size: 1.05rem;
  color: #555;
  line-height: 1.6;
}

/* ──── Section headers ──── */
.oi__section-title {
  font-size: 1.5rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0 0 6px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.oi__section-icon { font-size: 1.3rem; }
.oi__section-desc {
  font-size: 0.95rem;
  color: #666;
  margin: 0 0 24px;
  max-width: 600px;
  line-height: 1.55;
}

/* ──── Headline Stats (full-bleed) ──── */
.oi__headline-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.oi__headline-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.oi__headline-card {
  background: #fff;
  border-radius: 14px;
  padding: 24px 20px;
  text-align: center;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  border-top: 3px solid var(--hl-color);
  transition: transform 0.2s;
}
.oi__headline-card:hover { transform: translateY(-3px); }
.oi__headline-value {
  display: block;
  font-size: 1.8rem;
  font-weight: 900;
  color: var(--hl-color);
  letter-spacing: -0.02em;
}
.oi__headline-label {
  display: block;
  font-size: 0.88rem;
  font-weight: 700;
  color: #1a1a1a;
  margin: 4px 0 6px;
}
.oi__headline-desc {
  font-size: 0.8rem;
  color: #888;
  line-height: 1.45;
  margin: 0;
}

/* ──── Material Recovery ──── */
.oi__recovery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.oi__recovery-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.oi__recovery-card:hover { transform: translateY(-3px); }
.oi__recovery-name { font-size: 0.95rem; font-weight: 700; color: #1a1a1a; margin: 0 0 4px; }
.oi__recovery-amount {
  font-size: 1.2rem;
  font-weight: 900;
  color: var(--mat-color);
  display: block;
  margin-bottom: 10px;
}
.oi__recovery-bar {
  height: 6px;
  background: #eef0e8;
  border-radius: 3px;
  overflow: hidden;
}
.oi__recovery-fill {
  height: 100%;
  background: var(--mat-color);
  border-radius: 3px;
  transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}
.oi__recovery-pct { font-size: 0.74rem; color: #888; margin-top: 4px; display: block; }

/* ──── Environmental Savings (full-bleed) ──── */
.oi__savings-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.oi__savings-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.oi__saving-card {
  display: flex;
  gap: 16px;
  background: #fff;
  border-radius: 14px;
  padding: 22px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.oi__saving-card:hover { transform: translateY(-3px); }
.oi__saving-title { font-size: 0.98rem; font-weight: 700; color: #1a1a1a; margin: 0 0 2px; }
.oi__saving-value {
  font-size: 1.1rem;
  font-weight: 900;
  color: var(--color-green, #2f7a3e);
  display: block;
  margin-bottom: 6px;
}
.oi__saving-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── Project Highlights ──── */
.oi__projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}
.oi__project-card {
  background: #fff;
  border-radius: 16px;
  padding: 24px;
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}
.oi__project-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.1);
}
.oi__project-badge {
  display: inline-block;
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  padding: 3px 10px;
  border-radius: 10px;
  background: #e6f4ea;
  color: #1e7e34;
  margin-bottom: 10px;
}
.oi__project-title { font-size: 1.08rem; font-weight: 700; color: #1a1a1a; margin: 0 0 6px; }
.oi__project-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0 0 16px; }
.oi__project-stats {
  display: flex;
  gap: 16px;
}
.oi__project-stat { text-align: center; flex: 1; }
.oi__project-stat-value {
  display: block;
  font-size: 1.05rem;
  font-weight: 800;
  color: var(--color-green, #2f7a3e);
}
.oi__project-stat-label {
  font-size: 0.72rem;
  color: #999;
  display: block;
  margin-top: 2px;
}

/* ──── Goals (full-bleed) ──── */
.oi__goals-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.oi__goals-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.oi__goal-card {
  display: flex;
  gap: 18px;
  align-items: center;
  background: #fff;
  border-radius: 14px;
  padding: 22px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.oi__goal-card:hover { transform: translateY(-3px); }
.oi__goal-progress-ring {
  position: relative;
  width: 60px;
  height: 60px;
  flex-shrink: 0;
}
.oi__goal-progress-ring svg { width: 100%; height: 100%; }
.oi__goal-pct {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.78rem;
  font-weight: 800;
  color: var(--goal-color);
}
.oi__goal-title { font-size: 0.98rem; font-weight: 700; color: #1a1a1a; margin: 0 0 4px; }
.oi__goal-desc { font-size: 0.82rem; color: #777; line-height: 1.45; margin: 0; }

/* ──── How You Can Help ──── */
.oi__help-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  margin-bottom: 16px;
}
.oi__help-card {
  background: #fff;
  border-radius: 16px;
  padding: 28px 24px;
  border-top: 4px solid var(--help-accent);
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}
.oi__help-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.1);
}
.oi__help-title { font-size: 1.08rem; font-weight: 800; color: #1a1a1a; margin: 0 0 8px; }
.oi__help-desc { font-size: 0.86rem; color: #666; line-height: 1.55; margin: 0; }

/* ──── CTA Banner (full-bleed) ──── */
.oi__cta-banner {
  background: linear-gradient(135deg, var(--color-green-dark, #1f5a2b) 0%, var(--color-green, #2f7a3e) 50%, var(--color-brown, #6b4f32) 100%);
  border-radius: 0;
  padding: 64px 40px 80px;
  text-align: center;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  margin-top: -56px;
  padding-left: calc(50vw - 50% + 40px);
  padding-right: calc(50vw - 50% + 40px);
}
.oi__cta-inner { max-width: 520px; margin: 0 auto; }
.oi__cta-title { font-size: 1.6rem; font-weight: 800; color: #fff; margin: 0 0 8px; }
.oi__cta-desc { font-size: 1rem; color: rgba(255,255,255,0.85); margin: 0 0 24px; line-height: 1.5; }
.oi__cta-actions { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
.oi__cta-btn {
  display: inline-block;
  padding: 12px 28px;
  border-radius: 10px;
  font-size: 0.95rem;
  font-weight: 700;
  text-decoration: none;
  transition: transform 0.15s, box-shadow 0.2s;
}
.oi__cta-btn:hover { transform: translateY(-2px); box-shadow: 0 4px 16px rgba(0,0,0,0.2); }
.oi__cta-btn--primary { background: #fff; color: var(--color-green-dark, #1f5a2b); }
.oi__cta-btn--secondary { background: rgba(255,255,255,0.15); color: #fff; border: 1px solid rgba(255,255,255,0.3); }

/* ──── Responsive ──── */
@media (max-width: 900px) {
  .oi__headline-grid,
  .oi__recovery-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .oi { padding: 20px 16px 48px; }
  .oi__title { font-size: 1.5rem; }
  .oi__headline-grid,
  .oi__recovery-grid,
  .oi__savings-grid,
  .oi__projects-grid,
  .oi__goals-grid,
  .oi__help-grid { grid-template-columns: 1fr; }
  .oi__cta-banner { padding: 32px 20px; }
}
</style>
