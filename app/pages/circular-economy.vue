<template>
  <main class="ce">
    <div class="ce__container">

      <!-- ───── Hero ───── -->
      <section class="ce__hero">
        <span class="ce__badge">♻️ Circular Construction</span>
        <h1 class="ce__title">Circular Economy</h1>
        <p class="ce__subtitle">
          Rethinking construction from a linear "take-make-dispose" model to a
          regenerative system where materials circulate at their highest value
          — reducing waste, emissions and raw resource extraction across Denmark.
        </p>
      </section>

      <!-- ───── What Is It? (full-bleed) ───── -->
      <section class="ce__what-section">
        <h2 class="ce__section-title">
          <span class="ce__section-icon"></span>
          What Is a Circular Economy?
        </h2>
        <p class="ce__section-desc">
          Unlike the traditional linear model, a circular economy keeps products
          and materials in use for as long as possible, extracting maximum value
          before recovering and regenerating them.
        </p>
        <div class="ce__loop">
          <div v-for="(step, i) in loop" :key="step.title" class="ce__loop-step" :style="{ '--step-color': step.color }">
            <span class="ce__loop-num">{{ i + 1 }}</span>
            <div>
              <strong class="ce__loop-title">{{ step.title }}</strong>
              <p class="ce__loop-desc">{{ step.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Principles ───── -->
      <section class="ce__principles">
        <h2 class="ce__section-title">
          <span class="ce__section-icon"></span>
          Core Principles
        </h2>
        <p class="ce__section-desc">
          The Ellen MacArthur Foundation identifies three key principles that
          drive a circular economy in construction.
        </p>
        <div class="ce__principles-grid">
          <div v-for="p in principles" :key="p.title" class="ce__principle-card" :style="{ '--accent': p.color }">
            <h3 class="ce__principle-title">{{ p.title }}</h3>
            <p class="ce__principle-desc">{{ p.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── Benefits (full-bleed) ───── -->
      <section class="ce__benefits-section">
        <h2 class="ce__section-title">
          <span class="ce__section-icon"></span>
          Benefits for Construction
        </h2>
        <div class="ce__benefits-grid">
          <div v-for="b in benefits" :key="b.title" class="ce__benefit-card">
            <span class="ce__benefit-value">{{ b.value }}</span>
            <h3 class="ce__benefit-title">{{ b.title }}</h3>
            <p class="ce__benefit-desc">{{ b.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── Denmark in Focus ───── -->
      <section class="ce__denmark">
        <h2 class="ce__section-title">
          <span class="ce__section-icon"></span>
          Denmark Leading the Way
        </h2>
        <p class="ce__section-desc">
          Denmark is a frontrunner in circular construction, with national
          strategies and municipal initiatives pushing the industry forward.
        </p>
        <div class="ce__dk-grid">
          <div v-for="fact in dkFacts" :key="fact.title" class="ce__dk-card">
            <div class="ce__dk-badge">{{ fact.type }}</div>
            <h3 class="ce__dk-title">{{ fact.title }}</h3>
            <p class="ce__dk-desc">{{ fact.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── How Sortify Fits (full-bleed) ───── -->
      <section class="ce__sortify-section">
        <h2 class="ce__section-title">
          <span class="ce__section-icon"></span>
          How Sortify Enables Circularity
        </h2>
        <div class="ce__sortify-grid">
          <div v-for="s in sortifyRole" :key="s.title" class="ce__sortify-card">
            <span class="ce__sortify-num">{{ s.num }}</span>
            <div>
              <h3 class="ce__sortify-title">{{ s.title }}</h3>
              <p class="ce__sortify-desc">{{ s.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── CTA Banner ───── -->
      <section class="ce__cta-banner">
        <div class="ce__cta-inner">
          <h2 class="ce__cta-title">Close the loop with Sortify</h2>
          <p class="ce__cta-desc">
            Every material reused is a step toward a fully circular construction
            industry. Start making an impact today.
          </p>
          <div class="ce__cta-actions">
            <NuxtLink to="/marketplace" class="ce__cta-btn ce__cta-btn--primary">
              Browse Marketplace →
            </NuxtLink>
            <NuxtLink to="/about" class="ce__cta-btn ce__cta-btn--secondary">
              About Us
            </NuxtLink>
          </div>
        </div>
      </section>

    </div>
  </main>
</template>

<script setup lang="ts">
const loop = [
  { title: 'Design', desc: 'Plan buildings for disassembly and material recovery from day one.', color: '#2f7a3e' },
  { title: 'Build', desc: 'Use recycled, reclaimed and certified sustainable materials wherever possible.', color: '#22c55e' },
  { title: 'Use & Maintain', desc: 'Extend building lifespan through repair, renovation and adaptive reuse.', color: '#0e7490' },
  { title: 'Deconstruct', desc: 'Selectively disassemble rather than demolish — preserving material integrity.', color: '#6b4f32' },
  { title: 'Recover', desc: 'Sort, grade and register salvaged materials on platforms like Sortify.', color: '#b45309' },
  { title: 'Redistribute', desc: 'Connect recovered materials with new projects, completing the circle.', color: '#7c3aed' },
]

const principles = [
  {
    title: 'Eliminate Waste & Pollution', color: '#ef4444',
    desc: 'Design out waste from the start. Use modular construction, standardised dimensions and reversible connections to enable future disassembly.',
  },
  {
    title: 'Circulate Products & Materials', color: '#2f7a3e',
    desc: 'Keep materials in use at their highest value through reuse, refurbishment and high-quality recycling — exactly what Sortify facilitates.',
  },
  {
    title: 'Regenerate Nature', color: '#16a34a',
    desc: 'Shift to renewable inputs, return biological materials safely to the earth, and restore natural systems through responsible construction.',
  },
]

const benefits = [
  { value: '40%', title: 'Less Raw Material', desc: 'Circular practices can reduce virgin resource consumption by up to 40% in new builds.' },
  { value: '60%', title: 'Waste Reduction', desc: 'Selective demolition and material recovery can divert over 60% of construction waste from landfill.' },
  { value: '35%', title: 'Lower CO₂', desc: 'Reusing structural steel and concrete avoids the high embodied carbon of new production.' },
  { value: '25%', title: 'Cost Savings', desc: 'Reclaimed materials often cost 25-50% less than new equivalents, reducing project budgets.' },
  { value: '12×', title: 'More Jobs', desc: 'The circular economy generates up to 12 times more jobs per tonne than landfill disposal.' },
  { value: '70%', title: 'EU Target', desc: 'The EU Waste Framework Directive mandates 70% recovery of construction and demolition waste by weight.' },
]

const dkFacts = [
  {
    type: 'Strategy',
    title: 'National Circular Economy Strategy',
    desc: 'Denmark published its national strategy in 2018, setting ambitious targets for construction waste reduction and material reuse across all sectors.',
  },
  {
    type: 'Initiative',
    title: 'Circle House Project',
    desc: '60 social housing units in Lisbjerg built entirely with circular principles — every component designed for disassembly and future reuse.',
  },
  {
    type: 'Regulation',
    title: 'Climate Act 2020',
    desc: 'Denmark committed to 70% greenhouse gas reduction by 2030, driving the construction industry toward circular, low-carbon practices.',
  },
  {
    type: 'Municipal',
    title: 'Copenhagen 2025 Plan',
    desc: 'Copenhagen aims to become the world\'s first carbon-neutral capital, with circular construction as a key pillar of the plan.',
  },
]

const sortifyRole = [
  { num: '01', title: 'Material Registration', desc: 'Demolition teams register salvaged materials with photos, dimensions, condition ratings and GPS coordinates in real time.' },
  { num: '02', title: 'Marketplace Matching', desc: 'Our marketplace connects material supply from demolition sites with demand from new construction projects across Denmark.' },
  { num: '03', title: 'Impact Tracking', desc: 'Every transaction is measured — kilograms diverted, CO₂ saved, and reuse rates calculated automatically.' },
  { num: '04', title: 'Project Dashboards', desc: 'Demolition projects get live dashboards showing material inventories, registration progress and environmental impact.' },
  { num: '05', title: 'Quality Assurance', desc: 'Detailed material listings with photos and condition grades give buyers confidence in reclaimed materials.' },
  { num: '06', title: 'Regulatory Compliance', desc: 'Built-in reporting helps teams meet Danish waste management regulations and EU waste framework requirements.' },
]
</script>

<style scoped>
.ce {
  flex: 1;
  padding: 40px 24px 0;
  background: linear-gradient(175deg, #f6f7f3 0%, #eef0e8 100%);
}
.ce__container {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 56px;
}
.ce__container > :last-child {
  margin-bottom: -56px;
}

/* ──── Hero ──── */
.ce__hero { max-width: 680px; }
.ce__badge {
  display: inline-block;
  background: rgba(47,122,62,0.1);
  color: var(--color-green, #2f7a3e);
  font-size: 0.82rem;
  font-weight: 700;
  padding: 4px 14px;
  border-radius: 20px;
  margin-bottom: 10px;
}
.ce__title {
  font-size: 2.2rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0;
  letter-spacing: -0.02em;
}
.ce__subtitle {
  margin: 10px 0 0;
  font-size: 1.05rem;
  color: #555;
  line-height: 1.6;
}

/* ──── Section headers ──── */
.ce__section-title {
  font-size: 1.5rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0 0 6px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.ce__section-icon { font-size: 1.3rem; }
.ce__section-desc {
  font-size: 0.95rem;
  color: #666;
  margin: 0 0 24px;
  max-width: 600px;
  line-height: 1.55;
}

/* ──── What Is It (full-bleed) ──── */
.ce__what-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.ce__loop {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 640px;
}
.ce__loop-step {
  display: flex;
  align-items: center;
  gap: 16px;
  background: #fff;
  padding: 16px 20px;
  border-radius: 14px;
  border-left: 5px solid var(--step-color);
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s, box-shadow 0.2s;
}
.ce__loop-step:hover {
  transform: translateX(6px);
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
}
.ce__loop-num {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: var(--step-color);
  color: #fff;
  font-weight: 800;
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
.ce__loop-title { font-size: 1rem; color: #1a1a1a; }
.ce__loop-desc { font-size: 0.84rem; color: #777; margin: 2px 0 0; }

/* ──── Principles ──── */
.ce__principles-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.ce__principle-card {
  background: #fff;
  border-radius: 16px;
  padding: 28px 24px;
  border-top: 4px solid var(--accent);
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}
.ce__principle-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.1);
}
.ce__principle-icon { font-size: 2rem; display: block; margin-bottom: 10px; }
.ce__principle-title { font-size: 1.15rem; font-weight: 800; color: #1a1a1a; margin: 0 0 8px; }
.ce__principle-desc { font-size: 0.88rem; color: #666; line-height: 1.55; margin: 0; }

/* ──── Benefits (full-bleed) ──── */
.ce__benefits-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.ce__benefits-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.ce__benefit-card {
  background: #fff;
  border-radius: 14px;
  padding: 24px 20px;
  text-align: center;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.ce__benefit-card:hover { transform: translateY(-3px); }
.ce__benefit-value {
  display: block;
  font-size: 1.8rem;
  font-weight: 900;
  color: var(--color-green, #2f7a3e);
  letter-spacing: -0.02em;
}
.ce__benefit-title {
  font-size: 0.98rem;
  font-weight: 700;
  color: #1a1a1a;
  margin: 4px 0;
}
.ce__benefit-desc {
  font-size: 0.84rem;
  color: #777;
  line-height: 1.5;
  margin: 0;
}

/* ──── Denmark ──── */
.ce__dk-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}
.ce__dk-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.ce__dk-card:hover { transform: translateY(-3px); }
.ce__dk-badge {
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
.ce__dk-title { font-size: 1rem; font-weight: 700; color: #1a1a1a; margin: 0 0 6px; }
.ce__dk-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── How Sortify Fits (full-bleed) ──── */
.ce__sortify-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.ce__sortify-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.ce__sortify-card {
  display: flex;
  gap: 16px;
  background: #fff;
  border-radius: 14px;
  padding: 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.ce__sortify-card:hover { transform: translateY(-3px); }
.ce__sortify-num {
  font-size: 1.6rem;
  font-weight: 900;
  color: var(--color-green, #2f7a3e);
  opacity: 0.35;
  line-height: 1;
  flex-shrink: 0;
}
.ce__sortify-title { font-size: 0.98rem; font-weight: 700; color: #1a1a1a; margin: 0 0 4px; }
.ce__sortify-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── CTA Banner (full-bleed) ──── */
.ce__cta-banner {
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
.ce__cta-inner { max-width: 520px; margin: 0 auto; }
.ce__cta-title { font-size: 1.6rem; font-weight: 800; color: #fff; margin: 0 0 8px; }
.ce__cta-desc { font-size: 1rem; color: rgba(255,255,255,0.85); margin: 0 0 24px; line-height: 1.5; }
.ce__cta-actions { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
.ce__cta-btn {
  display: inline-block;
  padding: 12px 28px;
  border-radius: 10px;
  font-size: 0.95rem;
  font-weight: 700;
  text-decoration: none;
  transition: transform 0.15s, box-shadow 0.2s;
}
.ce__cta-btn:hover { transform: translateY(-2px); box-shadow: 0 4px 16px rgba(0,0,0,0.2); }
.ce__cta-btn--primary { background: #fff; color: var(--color-green-dark, #1f5a2b); }
.ce__cta-btn--secondary { background: rgba(255,255,255,0.15); color: #fff; border: 1px solid rgba(255,255,255,0.3); }

/* ──── Responsive ──── */
@media (max-width: 900px) {
  .ce__principles-grid,
  .ce__benefits-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .ce { padding: 20px 16px 48px; }
  .ce__title { font-size: 1.5rem; }
  .ce__principles-grid,
  .ce__benefits-grid,
  .ce__dk-grid,
  .ce__sortify-grid { grid-template-columns: 1fr; }
  .ce__cta-banner { padding: 32px 20px; }
}
</style>
