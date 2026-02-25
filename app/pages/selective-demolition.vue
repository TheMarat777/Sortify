<template>
  <main class="sd">
    <div class="sd__container">

      <!-- ───── Hero ───── -->
      <section class="sd__hero">
        <span class="sd__badge">🏗️ Deconstruction Science</span>
        <h1 class="sd__title">Selective Demolition</h1>
        <p class="sd__subtitle">
          The art and science of carefully dismantling buildings to preserve
          material value — maximising reuse, minimising waste, and keeping
          quality resources out of Danish landfills.
        </p>
      </section>

      <!-- ───── What Is It (full-bleed) ───── -->
      <section class="sd__what-section">
        <h2 class="sd__section-title">
          <span class="sd__section-icon"></span>
          What Is Selective Demolition?
        </h2>
        <p class="sd__section-desc">
          Unlike conventional demolition that crushes everything into mixed rubble,
          selective demolition systematically disassembles a building in reverse
          order of construction — preserving individual materials for reuse.
        </p>
        <div class="sd__compare">
          <div v-for="c in comparison" :key="c.title" class="sd__compare-card" :style="{ '--cmp-color': c.color }">
            <span class="sd__compare-label">{{ c.label }}</span>
            <h3 class="sd__compare-title">{{ c.title }}</h3>
            <ul class="sd__compare-list">
              <li v-for="item in c.items" :key="item">{{ item }}</li>
            </ul>
          </div>
        </div>
      </section>

      <!-- ───── Process Steps ───── -->
      <section class="sd__process">
        <h2 class="sd__section-title">
          <span class="sd__section-icon"></span>
          The Selective Demolition Process
        </h2>
        <p class="sd__section-desc">
          A structured approach ensures maximum material recovery and
          compliance with Danish environmental regulations.
        </p>
        <div class="sd__steps">
          <div v-for="(step, i) in steps" :key="step.title" class="sd__step-card">
            <div class="sd__step-num">{{ i + 1 }}</div>
            <div class="sd__step-body">
              <h3 class="sd__step-title">{{ step.title }}</h3>
              <p class="sd__step-desc">{{ step.desc }}</p>
              <div class="sd__step-tags">
                <span v-for="t in step.tags" :key="t" class="sd__step-tag">{{ t }}</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Materials Recovery (full-bleed) ───── -->
      <section class="sd__recovery-section">
        <h2 class="sd__section-title">
          <span class="sd__section-icon"></span>
          Material Recovery Rates
        </h2>
        <p class="sd__section-desc">
          Selective demolition dramatically increases the percentage of materials
          that can be reused or high-quality recycled.
        </p>
        <div class="sd__recovery-grid">
          <div v-for="m in materials" :key="m.name" class="sd__recovery-card" :style="{ '--mat-accent': m.accent }">
            <h3 class="sd__recovery-name">{{ m.name }}</h3>
            <div class="sd__recovery-bar-wrap">
              <div class="sd__recovery-bar">
                <div class="sd__recovery-fill" :style="{ width: m.selective }" />
              </div>
              <span class="sd__recovery-label">Selective: {{ m.selective }}</span>
            </div>
            <div class="sd__recovery-bar-wrap">
              <div class="sd__recovery-bar sd__recovery-bar--conv">
                <div class="sd__recovery-fill sd__recovery-fill--conv" :style="{ width: m.conventional }" />
              </div>
              <span class="sd__recovery-label sd__recovery-label--conv">Conventional: {{ m.conventional }}</span>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Best Practices ───── -->
      <section class="sd__practices">
        <h2 class="sd__section-title">
          <span class="sd__section-icon"></span>
          On-Site Best Practices
        </h2>
        <div class="sd__practices-grid">
          <div v-for="p in practices" :key="p.title" class="sd__practice-card">
            <span class="sd__practice-num">{{ p.num }}</span>
            <div>
              <h3 class="sd__practice-title">{{ p.title }}</h3>
              <p class="sd__practice-desc">{{ p.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Case Studies (full-bleed) ───── -->
      <section class="sd__cases-section">
        <h2 class="sd__section-title">
          <span class="sd__section-icon"></span>
          Danish Case Studies
        </h2>
        <div class="sd__cases-grid">
          <div v-for="cs in cases" :key="cs.title" class="sd__case-card">
            <div class="sd__case-badge">{{ cs.type }}</div>
            <h3 class="sd__case-title">{{ cs.title }}</h3>
            <p class="sd__case-desc">{{ cs.desc }}</p>
            <div class="sd__case-stats">
              <span v-for="st in cs.stats" :key="st" class="sd__case-stat">{{ st }}</span>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── CTA Banner ───── -->
      <section class="sd__cta-banner">
        <div class="sd__cta-inner">
          <h2 class="sd__cta-title">Deconstruct smarter with Sortify</h2>
          <p class="sd__cta-desc">
            Register recovered materials directly from your demolition site and
            connect with buyers across Denmark.
          </p>
          <div class="sd__cta-actions">
            <NuxtLink to="/dashboard" class="sd__cta-btn sd__cta-btn--primary">
              View Projects →
            </NuxtLink>
            <NuxtLink to="/marketplace" class="sd__cta-btn sd__cta-btn--secondary">
              Browse Marketplace
            </NuxtLink>
          </div>
        </div>
      </section>

    </div>
  </main>
</template>

<script setup lang="ts">
const comparison = [
  {
    label: 'Traditional', title: 'Conventional Demolition', color: '#ef4444',
    items: [
      'Wrecking ball or excavator crushes entire structure',
      'Mixed rubble sent to landfill or low-grade recycling',
      'Material value destroyed in the process',
      'High dust, noise and environmental impact',
      'Typically 15-30% material recovery rate',
    ],
  },
  {
    label: 'Modern', title: 'Selective Demolition', color: '#2f7a3e',
    items: [
      'Systematic disassembly in reverse construction order',
      'Individual materials sorted and graded on-site',
      'Material value preserved for direct reuse',
      'Controlled process with lower environmental impact',
      'Typically 70-90% material recovery rate',
    ],
  },
]

const steps = [
  {
    title: 'Pre-Demolition Audit',
    desc: 'A thorough building survey identifies all materials present, their condition, quantities and any hazardous substances like asbestos or lead paint.',
    tags: ['Survey', 'Hazard check', 'Material inventory'],
  },
  {
    title: 'Waste Management Plan',
    desc: 'A detailed plan is created specifying how each material type will be handled, sorted, stored and transported — required by Danish law for projects over 10 tonnes.',
    tags: ['Compliance', 'Sorting plan', 'Logistics'],
  },
  {
    title: 'Hazardous Material Removal',
    desc: 'Asbestos, PCBs, lead paint and other hazardous substances are carefully removed first by certified specialists following strict safety protocols.',
    tags: ['Safety', 'Certification', 'Containment'],
  },
  {
    title: 'Interior Stripping',
    desc: 'Fixtures, fittings, doors, windows, radiators and wiring are removed by hand — these items often have the highest direct reuse potential.',
    tags: ['Doors', 'Windows', 'Fixtures', 'Wiring'],
  },
  {
    title: 'Structural Disassembly',
    desc: 'Roof elements, steel beams, timber frames and masonry are carefully dismantled using cranes and specialized equipment to preserve integrity.',
    tags: ['Steel', 'Timber', 'Masonry', 'Cranes'],
  },
  {
    title: 'Material Registration',
    desc: 'All recovered materials are photographed, measured, graded and registered on Sortify — making them instantly available to buyers across Denmark.',
    tags: ['Sortify', 'Photos', 'Grading', 'Listing'],
  },
]

const materials = [
  { name: 'Structural Steel', selective: '95%', conventional: '40%', accent: '#374151' },
  { name: 'Timber & Wood', selective: '85%', conventional: '20%', accent: '#92400e' },
  { name: 'Bricks & Masonry', selective: '80%', conventional: '10%', accent: '#b45309' },
  { name: 'Windows & Doors', selective: '90%', conventional: '5%', accent: '#0e7490' },
  { name: 'Copper & Metals', selective: '98%', conventional: '55%', accent: '#7c3aed' },
  { name: 'Insulation', selective: '60%', conventional: '5%', accent: '#6b4f32' },
]

const practices = [
  { num: '01', title: 'Label everything', desc: 'Mark each material with origin, dimensions and condition. Clear labelling speeds up sorting and boosts buyer confidence.' },
  { num: '02', title: 'Separate sorting zones', desc: 'Designate clear areas for each material type. Use colour-coded containers and signage understood by all workers.' },
  { num: '03', title: 'Protect during removal', desc: 'Use soft slings for steel beams, stack timber on bearers, and wrap fragile items. Damage during handling destroys reuse value.' },
  { num: '04', title: 'Document as you go', desc: 'Take photos of materials in situ and after removal. Upload to Sortify immediately — the faster they are listed, the sooner they sell.' },
  { num: '05', title: 'Train the crew', desc: 'All workers should understand which materials have reuse value and how to handle them. A one-hour briefing can save tonnes of waste.' },
  { num: '06', title: 'Plan pickup logistics', desc: 'Coordinate with buyers early. Materials sitting on-site lose value and block access for ongoing demolition work.' },
]

const cases = [
  {
    type: 'Hospital',
    title: 'Aarhus University Hospital',
    desc: 'Selective demolition of the old hospital wing recovered over 3,200 tonnes of concrete, steel and timber for reuse in new campus buildings.',
    stats: ['3,200 t recovered', '82% reuse rate', '1,100 t CO₂ saved'],
  },
  {
    type: 'Industrial',
    title: 'Carlsberg Brewery Complex',
    desc: 'The historic brewery transformation preserved original brickwork, steel trusses and timber beams — integrating heritage materials into modern apartments.',
    stats: ['1,800 t heritage materials', '91% recovery', 'Cultural preservation'],
  },
  {
    type: 'Education',
    title: 'Frederiksberg School',
    desc: 'A pilot project demonstrating that even smaller demolitions benefit from selective methods — 180 windows and 400m of timber flooring were salvaged.',
    stats: ['180 windows saved', '400m flooring', '12 t metals'],
  },
  {
    type: 'Municipal',
    title: 'Aalborg Cement Factory',
    desc: 'The largest selective demolition in Northern Jutland. Massive steel structures and industrial-grade concrete were recovered for infrastructure projects.',
    stats: ['5,400 t total', '76% diverted', '28 weeks duration'],
  },
]
</script>

<style scoped>
.sd {
  flex: 1;
  padding: 40px 24px 0;
  background: linear-gradient(175deg, #f6f7f3 0%, #eef0e8 100%);
}
.sd__container {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 56px;
}
.sd__container > :last-child {
  margin-bottom: -56px;
}

/* ──── Hero ──── */
.sd__hero { max-width: 680px; }
.sd__badge {
  display: inline-block;
  background: rgba(47,122,62,0.1);
  color: var(--color-green, #2f7a3e);
  font-size: 0.82rem;
  font-weight: 700;
  padding: 4px 14px;
  border-radius: 20px;
  margin-bottom: 10px;
}
.sd__title {
  font-size: 2.2rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0;
  letter-spacing: -0.02em;
}
.sd__subtitle {
  margin: 10px 0 0;
  font-size: 1.05rem;
  color: #555;
  line-height: 1.6;
}

/* ──── Section headers ──── */
.sd__section-title {
  font-size: 1.5rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0 0 6px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.sd__section-icon { font-size: 1.3rem; }
.sd__section-desc {
  font-size: 0.95rem;
  color: #666;
  margin: 0 0 24px;
  max-width: 600px;
  line-height: 1.55;
}

/* ──── What Is It (full-bleed) ──── */
.sd__what-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.sd__compare {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}
.sd__compare-card {
  background: #fff;
  border-radius: 16px;
  padding: 28px 24px;
  border-top: 4px solid var(--cmp-color);
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}
.sd__compare-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.1);
}
.sd__compare-label {
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
.sd__compare-title { font-size: 1.15rem; font-weight: 800; color: #1a1a1a; margin: 0 0 12px; }
.sd__compare-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.sd__compare-list li {
  font-size: 0.86rem;
  color: #666;
  line-height: 1.45;
  padding-left: 18px;
  position: relative;
}
.sd__compare-list li::before {
  content: '';
  position: absolute;
  left: 0;
  top: 7px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--cmp-color);
  opacity: 0.5;
}

/* ──── Process Steps ──── */
.sd__steps {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.sd__step-card {
  display: flex;
  gap: 20px;
  background: #fff;
  border-radius: 16px;
  padding: 24px;
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}
.sd__step-card:hover {
  transform: translateX(6px);
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
}
.sd__step-num {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--color-green, #2f7a3e), var(--color-brown, #6b4f32));
  color: #fff;
  font-weight: 800;
  font-size: 1.1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
.sd__step-title { font-size: 1.05rem; font-weight: 700; color: #1a1a1a; margin: 0 0 4px; }
.sd__step-desc { font-size: 0.86rem; color: #777; line-height: 1.5; margin: 0 0 10px; }
.sd__step-tags { display: flex; flex-wrap: wrap; gap: 6px; }
.sd__step-tag {
  font-size: 0.72rem;
  font-weight: 600;
  padding: 3px 10px;
  border-radius: 20px;
  background: #f3f4f1;
  color: #555;
}

/* ──── Material Recovery (full-bleed) ──── */
.sd__recovery-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.sd__recovery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.sd__recovery-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.sd__recovery-card:hover { transform: translateY(-3px); }
.sd__recovery-name { font-size: 0.98rem; font-weight: 700; color: #1a1a1a; margin: 0 0 12px; }
.sd__recovery-bar-wrap { margin-bottom: 8px; }
.sd__recovery-bar {
  height: 8px;
  background: #eef0e8;
  border-radius: 4px;
  overflow: hidden;
}
.sd__recovery-bar--conv { background: #f3e8e8; }
.sd__recovery-fill {
  height: 100%;
  background: var(--mat-accent);
  border-radius: 4px;
  transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}
.sd__recovery-fill--conv { background: #ef4444; opacity: 0.5; }
.sd__recovery-label { font-size: 0.74rem; color: #777; margin-top: 3px; display: block; }
.sd__recovery-label--conv { color: #b91c1c; }

/* ──── Best Practices ──── */
.sd__practices-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}
.sd__practice-card {
  display: flex;
  gap: 16px;
  background: #fff;
  border-radius: 14px;
  padding: 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.sd__practice-card:hover { transform: translateY(-3px); }
.sd__practice-num {
  font-size: 1.6rem;
  font-weight: 900;
  color: var(--color-green, #2f7a3e);
  opacity: 0.35;
  line-height: 1;
  flex-shrink: 0;
}
.sd__practice-title { font-size: 0.98rem; font-weight: 700; color: #1a1a1a; margin: 0 0 4px; }
.sd__practice-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── Case Studies (full-bleed) ──── */
.sd__cases-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.sd__cases-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.sd__case-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.sd__case-card:hover { transform: translateY(-3px); }
.sd__case-badge {
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
.sd__case-title { font-size: 1rem; font-weight: 700; color: #1a1a1a; margin: 0 0 6px; }
.sd__case-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0 0 12px; }
.sd__case-stats { display: flex; flex-wrap: wrap; gap: 6px; }
.sd__case-stat {
  font-size: 0.72rem;
  font-weight: 600;
  padding: 3px 10px;
  border-radius: 20px;
  background: #f3f4f1;
  color: #555;
}

/* ──── CTA Banner (full-bleed) ──── */
.sd__cta-banner {
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
.sd__cta-inner { max-width: 520px; margin: 0 auto; }
.sd__cta-title { font-size: 1.6rem; font-weight: 800; color: #fff; margin: 0 0 8px; }
.sd__cta-desc { font-size: 1rem; color: rgba(255,255,255,0.85); margin: 0 0 24px; line-height: 1.5; }
.sd__cta-actions { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
.sd__cta-btn {
  display: inline-block;
  padding: 12px 28px;
  border-radius: 10px;
  font-size: 0.95rem;
  font-weight: 700;
  text-decoration: none;
  transition: transform 0.15s, box-shadow 0.2s;
}
.sd__cta-btn:hover { transform: translateY(-2px); box-shadow: 0 4px 16px rgba(0,0,0,0.2); }
.sd__cta-btn--primary { background: #fff; color: var(--color-green-dark, #1f5a2b); }
.sd__cta-btn--secondary { background: rgba(255,255,255,0.15); color: #fff; border: 1px solid rgba(255,255,255,0.3); }

/* ──── Responsive ──── */
@media (max-width: 900px) {
  .sd__compare,
  .sd__recovery-grid { grid-template-columns: 1fr; }
}
@media (max-width: 600px) {
  .sd { padding: 20px 16px 48px; }
  .sd__title { font-size: 1.5rem; }
  .sd__compare,
  .sd__recovery-grid,
  .sd__practices-grid,
  .sd__cases-grid { grid-template-columns: 1fr; }
  .sd__step-card { flex-direction: column; gap: 12px; }
  .sd__cta-banner { padding: 32px 20px; }
}
</style>
