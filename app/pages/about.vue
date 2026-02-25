<template>
  <main class="ab">
    <div class="ab__container">

      <!-- ───── Hero ───── -->
      <section class="ab__hero">
        <span class="ab__badge">🌱 Our Story</span>
        <h1 class="ab__title">About Sortify</h1>
        <p class="ab__subtitle">
          We're on a mission to eliminate construction waste in Denmark by
          connecting demolition projects with builders who need quality materials
          — turning rubble into resources.
        </p>
      </section>

      <!-- ───── Mission / Vision / Values ───── -->
      <section class="ab__pillars-section">
        <div class="ab__pillars">
          <div v-for="p in pillars" :key="p.title" class="ab__pillar-card" :style="{ '--pillar': p.color }">
            <img :src="p.img" :alt="p.title" class="ab__pillar-icon" />
            <h3 class="ab__pillar-title">{{ p.title }}</h3>
            <p class="ab__pillar-desc">{{ p.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── Impact Stats ───── -->
      <section class="ab__stats-section">
        <h2 class="ab__section-title">
          <span class="ab__section-icon"></span>
          Our Impact So Far
        </h2>
        <div class="ab__stats-grid">
          <div v-for="s in stats" :key="s.label" class="ab__stat-card">
            <span class="ab__stat-value">{{ s.value }}</span>
            <span class="ab__stat-label">{{ s.label }}</span>
          </div>
        </div>
      </section>

      <!-- ───── Timeline ───── -->
      <section class="ab__timeline-section">
        <h2 class="ab__section-title">
          <span class="ab__section-icon"></span>
          Our Journey
        </h2>
        <div class="ab__timeline">
          <div v-for="ev in timeline" :key="ev.year" class="ab__tl-item">
            <div class="ab__tl-dot" />
            <div class="ab__tl-content">
              <span class="ab__tl-year">{{ ev.year }}</span>
              <h3 class="ab__tl-title">{{ ev.title }}</h3>
              <p class="ab__tl-desc">{{ ev.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Team ───── -->
      <section class="ab__team-section">
        <h2 class="ab__section-title">
          <span class="ab__section-icon"></span>
          The Team
        </h2>
        <p class="ab__section-desc">
          A small, passionate team combining construction engineering knowledge
          with modern digital tools.
        </p>
        <div class="ab__team-grid">
          <div v-for="m in team" :key="m.name" class="ab__team-card">
            <div class="ab__team-avatar" :style="{ background: m.bg }">
              {{ m.initials }}
            </div>
            <h3 class="ab__team-name">{{ m.name }}</h3>
            <span class="ab__team-role">{{ m.role }}</span>
            <p class="ab__team-bio">{{ m.bio }}</p>
          </div>
        </div>
      </section>

      <!-- ───── Values ───── -->
      <section class="ab__values-section">
        <h2 class="ab__section-title">
          <span class="ab__section-icon"></span>
          What We Stand For
        </h2>
        <div class="ab__values-grid">
          <div v-for="v in values" :key="v.title" class="ab__value-card">
            <h3 class="ab__value-title">{{ v.title }}</h3>
            <p class="ab__value-desc">{{ v.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── CTA Banner ───── -->
      <section class="ab__cta-banner">
        <div class="ab__cta-inner">
          <h2 class="ab__cta-title">Join the circular construction movement</h2>
          <p class="ab__cta-desc">
            Whether you're a demolition contractor, builder, architect or municipality —
            there's a place for you on Sortify.
          </p>
          <div class="ab__cta-actions">
            <NuxtLink to="/marketplace" class="ab__cta-btn ab__cta-btn--primary">
              Explore Marketplace →
            </NuxtLink>
            <NuxtLink to="/recycling-guide" class="ab__cta-btn ab__cta-btn--secondary">
              Recycling Guide
            </NuxtLink>
          </div>
        </div>
      </section>

    </div>
  </main>
</template>

<script setup lang="ts">
import missionImg from '../../assets/images/Target, checklist and lightbulb icon.png'
import visionImg from '../../assets/images/Sustainable vision and growth icon.png'
import promiseImg from '../../assets/images/Handshake of trust and growth.png'

const pillars = [
  {
    img: missionImg, title: 'Mission', color: '#2f7a3e',
    desc: 'To make construction material reuse the default choice in Denmark, cutting landfill waste by connecting supply with demand in real time.',
  },
  {
    img: visionImg, title: 'Vision', color: '#0e7490',
    desc: 'A Danish construction industry where every demolition project feeds the next build — zero waste, full circularity.',
  },
  {
    img: promiseImg, title: 'Promise', color: '#6b4f32',
    desc: 'Transparent data, honest listings, and measurable environmental impact for every material that passes through the platform.',
  },
]

const stats = [
  { value: '92,240 kg', label: 'Materials registered' },
  { value: '6', label: 'Active projects' },
  { value: '74', label: 'Materials listed' },
  { value: '61%', label: 'Average reuse rate' },
  { value: '38 t', label: 'CO₂ saved (est.)' },
  { value: '12', label: 'Danish municipalities' },
]

const timeline = [
  { year: '2024', title: 'The idea', desc: 'Concept born during a sustainability workshop at the Technical University of Denmark.' },
  { year: 'Early 2025', title: 'Research & validation', desc: 'Interviews with demolition companies, municipalities and builders across Sjælland and Jylland.' },
  { year: 'Mid 2025', title: 'Prototype launch', desc: 'First working version with material registration, marketplace and project tracking.' },
  { year: 'Late 2025', title: 'Pilot projects', desc: 'Partnerships with Aalborg Cement Factory and Frederiksberg School for real-world testing.' },
  { year: '2026', title: 'Growth phase', desc: 'Six active demolition projects, marketplace with 70+ materials, and growing community of reuse advocates.' },
]

const team = [
  { name: 'Marat Colesnic', initials: 'MC', role: 'Software Engineer', bg: '#2f7a3e', bio: 'Frontend engineer who brought the Sortify interface to life — from marketplace layouts to interactive dashboards and responsive design.' },
  { name: 'Andreea Caisim', initials: 'AC', role: 'Software Engineer', bg: '#2f7a3e', bio: 'Frontend developer responsible for crafting the UI components, styling and user experience across the platform.' },
  { name: 'Marius Marcoci', initials: 'MM', role: 'Software Engineer', bg: '#2f7a3e', bio: 'Database engineer who designed and maintained the data layer — structuring material records, project data and user information.' },
  { name: 'Ashrakat Sh Ibrahim', initials: 'ASI', role: 'Civil Engineer', bg: '#b45309', bio: 'Civil engineer focused on sustainable building practices, waste auditing and ensuring compliance with Danish demolition regulations.' },
  { name: 'Helena Thybo Cavazzi', initials: 'HTC', role: 'Civil Engineer', bg: '#b45309', bio: 'Structural engineer with expertise in material assessment, selective demolition planning and construction lifecycle analysis.' },
  { name: 'Kasper Gjesse', initials: 'KG', role: 'Civil Engineer', bg: '#b45309', bio: 'Civil engineer specialising in on-site material recovery, quality documentation and coordinating reuse logistics for demolition projects.' },
]

const values = [
  { title: 'Circularity First', desc: 'Every decision is measured against its impact on material reuse and waste reduction.' },
  { title: 'Data-Driven', desc: 'Real numbers, real weights, real impact. We track every kilogram that avoids the landfill.' },
  { title: 'Industry-Ready', desc: 'Built for the people who work on site — intuitive, fast and practical.' },
  { title: 'Open & Transparent', desc: 'Public dashboards, open data, honest reporting of environmental savings.' },
  { title: 'Locally Rooted', desc: 'Designed for Danish regulations, logistics and construction culture from day one.' },
  { title: 'Always Improving', desc: 'We ship fast, learn from every project and iterate based on real user feedback.' },
]
</script>

<style scoped>
.ab {
  flex: 1;
  padding: 40px 24px 0;
  background: linear-gradient(175deg, #f6f7f3 0%, #eef0e8 100%);
}
.ab__container {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 56px;
}

/* remove gap after last child so CTA sits flush with footer */
.ab__container > :last-child {
  margin-bottom: -56px;
}

/* ──── Hero ──── */
.ab__hero { max-width: 680px; }
.ab__badge {
  display: inline-block;
  background: rgba(47,122,62,0.1);
  color: var(--color-green, #2f7a3e);
  font-size: 0.82rem;
  font-weight: 700;
  padding: 4px 14px;
  border-radius: 20px;
  margin-bottom: 10px;
}
.ab__title {
  font-size: 2.2rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0;
  letter-spacing: -0.02em;
}
.ab__subtitle {
  margin: 10px 0 0;
  font-size: 1.05rem;
  color: #555;
  line-height: 1.6;
}

/* ──── Section headers ──── */
.ab__section-title {
  font-size: 1.5rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0 0 6px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.ab__section-icon { font-size: 1.3rem; }
.ab__section-desc {
  font-size: 0.95rem;
  color: #666;
  margin: 0 0 24px;
  max-width: 600px;
  line-height: 1.55;
}

/* ──── Pillars (full-bleed brown layer) ──── */
.ab__pillars-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.ab__pillars {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.ab__pillar-card {
  background: #fff;
  border-radius: 16px;
  padding: 28px 24px;
  border-top: 4px solid var(--pillar);
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  transition: transform 0.2s, box-shadow 0.2s;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.ab__pillar-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.1);
}
.ab__pillar-icon {
  width: 150px;
  height: 150px;
  object-fit: contain;
  display: block;
  margin-bottom: 14px;
  border-radius: 12px;
}
.ab__pillar-title { font-size: 1.15rem; font-weight: 800; color: #1a1a1a; margin: 0 0 8px; }
.ab__pillar-desc { font-size: 0.88rem; color: #666; line-height: 1.55; margin: 0; }

/* ──── Impact Stats ──── */
.ab__stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.ab__stat-card {
  background: #fff;
  border-radius: 14px;
  padding: 24px 20px;
  text-align: center;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.ab__stat-card:hover { transform: translateY(-3px); }
.ab__stat-value {
  display: block;
  font-size: 1.8rem;
  font-weight: 900;
  color: var(--color-green, #2f7a3e);
  letter-spacing: -0.02em;
}
.ab__stat-label {
  display: block;
  font-size: 0.84rem;
  color: #777;
  margin-top: 4px;
}

/* ──── Timeline (full-bleed brown layer) ──── */
.ab__timeline-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.ab__timeline {
  position: relative;
  padding-left: 32px;
  margin-top: 20px;
}
.ab__timeline::before {
  content: '';
  position: absolute;
  left: 7px;
  top: 0;
  bottom: 0;
  width: 3px;
  background: linear-gradient(to bottom, var(--color-green, #2f7a3e), var(--color-brown, #6b4f32));
  border-radius: 2px;
}
.ab__tl-item {
  position: relative;
  padding-bottom: 32px;
}
.ab__tl-item:last-child { padding-bottom: 0; }
.ab__tl-dot {
  position: absolute;
  left: -29px;
  top: 4px;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: var(--color-green, #2f7a3e);
  border: 3px solid #f5efe6;
  box-shadow: 0 0 0 2px var(--color-green, #2f7a3e);
}
.ab__tl-content {
  background: #fff;
  border-radius: 14px;
  padding: 18px 22px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.ab__tl-content:hover { transform: translateX(4px); }
.ab__tl-year {
  font-size: 0.76rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: var(--color-green, #2f7a3e);
}
.ab__tl-title { font-size: 1.05rem; font-weight: 700; color: #1a1a1a; margin: 4px 0 4px; }
.ab__tl-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── Team ──── */
.ab__team-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}
.ab__team-card {
  background: #fff;
  border-radius: 16px;
  padding: 28px 20px 22px;
  text-align: center;
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}
.ab__team-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.1);
}
.ab__team-avatar {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  color: #fff;
  font-weight: 800;
  font-size: 1.2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 14px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}
.ab__team-name { font-size: 1rem; font-weight: 700; color: #1a1a1a; margin: 0 0 2px; }
.ab__team-role {
  font-size: 0.78rem;
  font-weight: 600;
  color: var(--color-green, #2f7a3e);
  display: block;
  margin-bottom: 8px;
}
.ab__team-bio { font-size: 0.82rem; color: #888; line-height: 1.45; margin: 0; }

/* ──── Values (full-bleed brown layer) ──── */
.ab__values-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.ab__values-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.ab__value-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.ab__value-card:hover { transform: translateY(-3px); }
.ab__value-title {
  font-size: 0.98rem;
  font-weight: 700;
  color: #1a1a1a;
  margin: 0 0 4px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.ab__value-title::before {
  content: '';
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--color-green, #2f7a3e);
  flex-shrink: 0;
}
.ab__value-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── CTA Banner (full-bleed) ──── */
.ab__cta-banner {
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
.ab__cta-inner { max-width: 520px; margin: 0 auto; }
.ab__cta-title { font-size: 1.6rem; font-weight: 800; color: #fff; margin: 0 0 8px; }
.ab__cta-desc { font-size: 1rem; color: rgba(255,255,255,0.85); margin: 0 0 24px; line-height: 1.5; }
.ab__cta-actions { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
.ab__cta-btn {
  display: inline-block;
  padding: 12px 28px;
  border-radius: 10px;
  font-size: 0.95rem;
  font-weight: 700;
  text-decoration: none;
  transition: transform 0.15s, box-shadow 0.2s;
}
.ab__cta-btn:hover { transform: translateY(-2px); box-shadow: 0 4px 16px rgba(0,0,0,0.2); }
.ab__cta-btn--primary { background: #fff; color: var(--color-green-dark, #1f5a2b); }
.ab__cta-btn--secondary { background: rgba(255,255,255,0.15); color: #fff; border: 1px solid rgba(255,255,255,0.3); }

/* ──── Responsive ──── */
@media (max-width: 900px) {
  .ab__pillars,
  .ab__stats-grid,
  .ab__values-grid { grid-template-columns: repeat(2, 1fr); }
  .ab__team-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .ab { padding: 20px 16px 48px; }
  .ab__title { font-size: 1.5rem; }
  .ab__pillars,
  .ab__stats-grid,
  .ab__values-grid,
  .ab__team-grid { grid-template-columns: 1fr; }
  .ab__cta-banner { padding: 32px 20px; }
}
</style>
