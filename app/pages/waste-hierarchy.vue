<template>
  <main class="wh">
    <div class="wh__container">

      <!-- ───── Hero ───── -->
      <section class="wh__hero">
        <span class="wh__badge">🔺 Waste Management</span>
        <h1 class="wh__title">Waste Hierarchy</h1>
        <p class="wh__subtitle">
          The EU Waste Framework Directive establishes a five-tier priority order
          for managing construction waste — from prevention at the top to disposal
          as a last resort. Sortify focuses on the top three tiers.
        </p>
      </section>

      <!-- ───── The Pyramid (full-bleed) ───── -->
      <section class="wh__pyramid-section">
        <h2 class="wh__section-title">
          <span class="wh__section-icon"></span>
          The Five Tiers
        </h2>
        <p class="wh__section-desc">
          Each tier is preferred over the ones below it. Moving waste management
          up the hierarchy reduces environmental impact exponentially.
        </p>
        <div class="wh__pyramid">
          <div
            v-for="(tier, i) in tiers"
            :key="tier.title"
            class="wh__tier"
            :style="{ '--tier-color': tier.color, '--tier-width': tier.width }"
          >
            <div class="wh__tier-rank">{{ i + 1 }}</div>
            <div class="wh__tier-body">
              <strong class="wh__tier-title">{{ tier.title }}</strong>
              <p class="wh__tier-desc">{{ tier.desc }}</p>
              <div class="wh__tier-examples">
                <span v-for="ex in tier.examples" :key="ex" class="wh__tier-tag">{{ ex }}</span>
              </div>
            </div>
            <div class="wh__tier-impact">
              <span class="wh__tier-impact-label">Impact</span>
              <span class="wh__tier-impact-value" :style="{ color: tier.color }">{{ tier.impact }}</span>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Prevention Deep Dive ───── -->
      <section class="wh__prevention">
        <h2 class="wh__section-title">
          <span class="wh__section-icon"></span>
          Tier 1: Prevention
        </h2>
        <p class="wh__section-desc">
          The most effective waste strategy is generating no waste at all.
          Prevention happens at the design and planning stage.
        </p>
        <div class="wh__prevention-grid">
          <div v-for="p in prevention" :key="p.title" class="wh__prevention-card" :style="{ '--accent': p.color }">
            <h3 class="wh__prevention-title">{{ p.title }}</h3>
            <p class="wh__prevention-desc">{{ p.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── Reuse & Recycling (full-bleed) ───── -->
      <section class="wh__reuse-section">
        <h2 class="wh__section-title">
          <span class="wh__section-icon"></span>
          Tiers 2 & 3: Reuse & Recycling
        </h2>
        <p class="wh__section-desc">
          Where Sortify makes the biggest difference — connecting salvaged materials
          with new projects and ensuring high-quality recycling.
        </p>
        <div class="wh__reuse-grid">
          <div v-for="r in reuseItems" :key="r.title" class="wh__reuse-card">
            <span class="wh__reuse-num">{{ r.num }}</span>
            <div>
              <h3 class="wh__reuse-title">{{ r.title }}</h3>
              <p class="wh__reuse-desc">{{ r.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Material Breakdown ───── -->
      <section class="wh__materials">
        <h2 class="wh__section-title">
          <span class="wh__section-icon"></span>
          Construction Waste by Material
        </h2>
        <p class="wh__section-desc">
          Understanding the composition of construction and demolition waste
          helps prioritise which materials to target first.
        </p>
        <div class="wh__materials-grid">
          <div v-for="m in materialBreakdown" :key="m.name" class="wh__material-card" :style="{ '--mat-color': m.color }">
            <div class="wh__material-pct">{{ m.pct }}</div>
            <h3 class="wh__material-name">{{ m.name }}</h3>
            <p class="wh__material-desc">{{ m.desc }}</p>
            <div class="wh__material-bar">
              <div class="wh__material-fill" :style="{ width: m.pct }" />
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Danish Context (full-bleed) ───── -->
      <section class="wh__danish-section">
        <h2 class="wh__section-title">
          <span class="wh__section-icon"></span>
          The Danish Framework
        </h2>
        <div class="wh__danish-grid">
          <div v-for="d in danishContext" :key="d.title" class="wh__danish-card">
            <div class="wh__danish-badge">{{ d.type }}</div>
            <h3 class="wh__danish-title">{{ d.title }}</h3>
            <p class="wh__danish-desc">{{ d.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── Key Statistics ───── -->
      <section class="wh__stats">
        <h2 class="wh__section-title">
          <span class="wh__section-icon"></span>
          Key Numbers
        </h2>
        <div class="wh__stats-grid">
          <div v-for="s in stats" :key="s.label" class="wh__stat-card">
            <span class="wh__stat-value">{{ s.value }}</span>
            <span class="wh__stat-label">{{ s.label }}</span>
          </div>
        </div>
      </section>

      <!-- ───── CTA Banner ───── -->
      <section class="wh__cta-banner">
        <div class="wh__cta-inner">
          <h2 class="wh__cta-title">Move your waste management up the hierarchy</h2>
          <p class="wh__cta-desc">
            Sortify helps you prioritise reuse and recycling over disposal —
            turning demolition waste into valuable building resources.
          </p>
          <div class="wh__cta-actions">
            <NuxtLink to="/marketplace" class="wh__cta-btn wh__cta-btn--primary">
              Browse Marketplace →
            </NuxtLink>
            <NuxtLink to="/recycling-guide" class="wh__cta-btn wh__cta-btn--secondary">
              Recycling Guide
            </NuxtLink>
          </div>
        </div>
      </section>

    </div>
  </main>
</template>

<script setup lang="ts">
const tiers = [
  {
    title: 'Prevention', color: '#16a34a', width: '50%', impact: 'Highest',
    desc: 'Avoid generating waste in the first place through better design, lean construction and accurate ordering.',
    examples: ['Design for disassembly', 'Modular construction', 'Accurate BIM ordering'],
  },
  {
    title: 'Preparing for Reuse', color: '#22c55e', width: '60%', impact: 'Very High',
    desc: 'Check, clean and repair products or components so they can be reused without reprocessing.',
    examples: ['Salvaged doors & windows', 'Reclaimed timber', 'Reused steel beams'],
  },
  {
    title: 'Recycling', color: '#86efac', width: '70%', impact: 'High',
    desc: 'Process waste materials into new raw inputs — crushed concrete as aggregate, metal smelting, glass cullet.',
    examples: ['Concrete crushing', 'Metal smelting', 'Glass recycling'],
  },
  {
    title: 'Other Recovery', color: '#fbbf24', width: '80%', impact: 'Moderate',
    desc: 'Extract energy or materials from waste through incineration with energy recovery or backfilling.',
    examples: ['Waste-to-energy', 'Backfilling', 'Biomass from timber'],
  },
  {
    title: 'Disposal', color: '#ef4444', width: '90%', impact: 'Lowest',
    desc: 'Landfill or incineration without energy recovery. The least preferred and most environmentally harmful option.',
    examples: ['Landfill', 'Hazardous waste storage', 'Last resort only'],
  },
]

const prevention = [
  {
    title: 'Design for Disassembly', color: '#2f7a3e',
    desc: 'Use reversible connections, standardised dimensions and modular systems that can be taken apart cleanly at end of life.',
  },
  {
    title: 'Lean Construction', color: '#0e7490',
    desc: 'Minimise material waste during construction through just-in-time delivery, precise cutting and prefabrication.',
  },
  {
    title: 'BIM & Digital Twins', color: '#7c3aed',
    desc: 'Use Building Information Modelling to order exact quantities, reducing over-ordering and offcut waste by up to 30%.',
  },
  {
    title: 'Material Passports', color: '#b45309',
    desc: 'Document every material used in a building so it can be identified, valued and recovered at end of life.',
  },
  {
    title: 'Pre-demolition Audits', color: '#6b4f32',
    desc: 'Survey buildings before demolition to plan which materials can be salvaged, reused or recycled.',
  },
  {
    title: 'Supply Chain Collaboration', color: '#374151',
    desc: 'Work with suppliers to take back packaging, pallets and unused materials — closing the loop before waste is generated.',
  },
]

const reuseItems = [
  { num: '01', title: 'Direct reuse on-site', desc: 'Salvaged materials from one part of a demolition project used directly in new construction on the same site.' },
  { num: '02', title: 'Marketplace redistribution', desc: 'List recovered materials on Sortify to find buyers across Denmark — extending reach beyond the immediate project.' },
  { num: '03', title: 'Quality grading', desc: 'Grade materials by condition (A/B/C) to set buyer expectations and ensure structural integrity for reuse applications.' },
  { num: '04', title: 'Certified recycling facilities', desc: 'Materials that cannot be directly reused are sent to certified facilities for high-quality recycling into new raw materials.' },
  { num: '05', title: 'Downcycling avoidance', desc: 'Prioritise applications that maintain material quality — crushed concrete as structural aggregate rather than low-grade fill.' },
  { num: '06', title: 'Impact measurement', desc: 'Track kilograms reused vs. recycled vs. disposed to continuously improve your waste hierarchy performance.' },
]

const materialBreakdown = [
  { name: 'Concrete & Masonry', pct: '45%', color: '#6b7280', desc: 'The largest fraction by weight. Easily crushed for aggregate reuse in road base and new concrete.' },
  { name: 'Timber & Wood', pct: '20%', color: '#92400e', desc: 'Untreated timber has high reuse potential. Treated wood requires special handling or energy recovery.' },
  { name: 'Metals', pct: '12%', color: '#374151', desc: 'Highest recycling rates of any construction material. Steel and copper retain quality through infinite recycling.' },
  { name: 'Mixed Waste', pct: '10%', color: '#7c3aed', desc: 'Plasterboard, plastic, packaging and composites. Harder to recycle but improving with better sorting technology.' },
  { name: 'Soil & Aggregates', pct: '8%', color: '#b45309', desc: 'Clean soil can be reused on-site. Contaminated soil requires remediation before any further use.' },
  { name: 'Hazardous', pct: '5%', color: '#ef4444', desc: 'Asbestos, PCBs, lead paint. Must be handled by certified specialists and cannot enter the reuse stream.' },
]

const danishContext = [
  {
    type: 'EU Directive',
    title: 'Waste Framework 2008/98/EC',
    desc: 'Establishes the waste hierarchy as the guiding principle for all EU waste legislation. Mandates 70% recovery of C&D waste by weight.',
  },
  {
    type: 'National',
    title: 'Affaldsbekendtgorelsen',
    desc: 'The Danish Waste Statutory Order requires waste producers to sort construction waste into minimum fractions and report to the national waste database.',
  },
  {
    type: 'Strategy',
    title: 'Denmark Without Waste II',
    desc: 'National waste prevention strategy targeting higher material recovery rates and reduced landfill dependency through circular economy principles.',
  },
  {
    type: 'Municipal',
    title: 'Kommunal Affaldsplan',
    desc: 'Each of Denmark\'s 98 municipalities maintains a waste management plan with specific targets for construction waste sorting and recovery.',
  },
]

const stats = [
  { value: '4.2M t', label: 'C&D waste generated in Denmark per year' },
  { value: '87%', label: 'Current Danish recovery rate (one of EU highest)' },
  { value: '70%', label: 'EU minimum recovery target for C&D waste' },
  { value: '30%', label: 'Waste reduced by BIM-based ordering' },
  { value: '95%', label: 'Metal recycling rate achievable' },
  { value: '12×', label: 'More jobs in reuse vs. landfill per tonne' },
]
</script>

<style scoped>
.wh {
  flex: 1;
  padding: 40px 24px 0;
  background: linear-gradient(175deg, #f6f7f3 0%, #eef0e8 100%);
}
.wh__container {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 56px;
}
.wh__container > :last-child {
  margin-bottom: -56px;
}

/* ──── Hero ──── */
.wh__hero { max-width: 680px; }
.wh__badge {
  display: inline-block;
  background: rgba(47,122,62,0.1);
  color: var(--color-green, #2f7a3e);
  font-size: 0.82rem;
  font-weight: 700;
  padding: 4px 14px;
  border-radius: 20px;
  margin-bottom: 10px;
}
.wh__title {
  font-size: 2.2rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0;
  letter-spacing: -0.02em;
}
.wh__subtitle {
  margin: 10px 0 0;
  font-size: 1.05rem;
  color: #555;
  line-height: 1.6;
}

/* ──── Section headers ──── */
.wh__section-title {
  font-size: 1.5rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0 0 6px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.wh__section-icon { font-size: 1.3rem; }
.wh__section-desc {
  font-size: 0.95rem;
  color: #666;
  margin: 0 0 24px;
  max-width: 600px;
  line-height: 1.55;
}

/* ──── Pyramid (full-bleed) ──── */
.wh__pyramid-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.wh__pyramid {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-top: 8px;
}
.wh__tier {
  display: flex;
  align-items: flex-start;
  gap: 16px;
  background: #fff;
  padding: 20px 22px;
  border-radius: 14px;
  border-left: 5px solid var(--tier-color);
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s, box-shadow 0.2s;
}
.wh__tier:hover {
  transform: translateX(6px);
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
}
.wh__tier-rank {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: var(--tier-color);
  color: #fff;
  font-weight: 800;
  font-size: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
.wh__tier-body { flex: 1; }
.wh__tier-title { font-size: 1.05rem; color: #1a1a1a; display: block; margin-bottom: 4px; }
.wh__tier-desc { font-size: 0.84rem; color: #777; margin: 0 0 10px; line-height: 1.5; }
.wh__tier-examples { display: flex; flex-wrap: wrap; gap: 6px; }
.wh__tier-tag {
  font-size: 0.72rem;
  font-weight: 600;
  padding: 3px 10px;
  border-radius: 20px;
  background: #f3f4f1;
  color: #555;
}
.wh__tier-impact {
  text-align: center;
  flex-shrink: 0;
  min-width: 70px;
}
.wh__tier-impact-label { font-size: 0.68rem; color: #aaa; display: block; text-transform: uppercase; letter-spacing: 0.06em; }
.wh__tier-impact-value { font-size: 0.82rem; font-weight: 800; display: block; margin-top: 2px; }

/* ──── Prevention ──── */
.wh__prevention-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.wh__prevention-card {
  background: #fff;
  border-radius: 16px;
  padding: 28px 24px;
  border-top: 4px solid var(--accent);
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}
.wh__prevention-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.1);
}
.wh__prevention-title { font-size: 1.05rem; font-weight: 800; color: #1a1a1a; margin: 0 0 8px; }
.wh__prevention-desc { font-size: 0.86rem; color: #666; line-height: 1.55; margin: 0; }

/* ──── Reuse & Recycling (full-bleed) ──── */
.wh__reuse-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.wh__reuse-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.wh__reuse-card {
  display: flex;
  gap: 16px;
  background: #fff;
  border-radius: 14px;
  padding: 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.wh__reuse-card:hover { transform: translateY(-3px); }
.wh__reuse-num {
  font-size: 1.6rem;
  font-weight: 900;
  color: var(--color-green, #2f7a3e);
  opacity: 0.35;
  line-height: 1;
  flex-shrink: 0;
}
.wh__reuse-title { font-size: 0.98rem; font-weight: 700; color: #1a1a1a; margin: 0 0 4px; }
.wh__reuse-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── Material Breakdown ──── */
.wh__materials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.wh__material-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.wh__material-card:hover { transform: translateY(-3px); }
.wh__material-pct {
  font-size: 1.8rem;
  font-weight: 900;
  color: var(--mat-color);
  letter-spacing: -0.02em;
}
.wh__material-name { font-size: 0.98rem; font-weight: 700; color: #1a1a1a; margin: 4px 0; }
.wh__material-desc { font-size: 0.82rem; color: #777; line-height: 1.5; margin: 0 0 10px; }
.wh__material-bar {
  height: 6px;
  background: #eef0e8;
  border-radius: 3px;
  overflow: hidden;
}
.wh__material-fill {
  height: 100%;
  background: var(--mat-color);
  border-radius: 3px;
  transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

/* ──── Danish Context (full-bleed) ──── */
.wh__danish-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.wh__danish-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.wh__danish-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.wh__danish-card:hover { transform: translateY(-3px); }
.wh__danish-badge {
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
.wh__danish-title { font-size: 1rem; font-weight: 700; color: #1a1a1a; margin: 0 0 6px; }
.wh__danish-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── Key Stats ──── */
.wh__stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-top: 20px;
}
.wh__stat-card {
  background: #fff;
  border-radius: 14px;
  padding: 24px 20px;
  text-align: center;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.wh__stat-card:hover { transform: translateY(-3px); }
.wh__stats-grid { margin-bottom: 16px; }
.wh__stat-value {
  display: block;
  font-size: 1.8rem;
  font-weight: 900;
  color: var(--color-green, #2f7a3e);
  letter-spacing: -0.02em;
}
.wh__stat-label {
  display: block;
  font-size: 0.84rem;
  color: #777;
  margin-top: 4px;
}

/* ──── CTA Banner (full-bleed) ──── */
.wh__cta-banner {
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
.wh__cta-inner { max-width: 520px; margin: 0 auto; }
.wh__cta-title { font-size: 1.6rem; font-weight: 800; color: #fff; margin: 0 0 8px; }
.wh__cta-desc { font-size: 1rem; color: rgba(255,255,255,0.85); margin: 0 0 24px; line-height: 1.5; }
.wh__cta-actions { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
.wh__cta-btn {
  display: inline-block;
  padding: 12px 28px;
  border-radius: 10px;
  font-size: 0.95rem;
  font-weight: 700;
  text-decoration: none;
  transition: transform 0.15s, box-shadow 0.2s;
}
.wh__cta-btn:hover { transform: translateY(-2px); box-shadow: 0 4px 16px rgba(0,0,0,0.2); }
.wh__cta-btn--primary { background: #fff; color: var(--color-green-dark, #1f5a2b); }
.wh__cta-btn--secondary { background: rgba(255,255,255,0.15); color: #fff; border: 1px solid rgba(255,255,255,0.3); }

/* ──── Responsive ──── */
@media (max-width: 900px) {
  .wh__prevention-grid,
  .wh__materials-grid,
  .wh__stats-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .wh { padding: 20px 16px 48px; }
  .wh__title { font-size: 1.5rem; }
  .wh__prevention-grid,
  .wh__materials-grid,
  .wh__stats-grid,
  .wh__reuse-grid,
  .wh__danish-grid { grid-template-columns: 1fr; }
  .wh__tier { flex-direction: column; gap: 12px; }
  .wh__tier-impact { text-align: left; }
  .wh__cta-banner { padding: 32px 20px; }
}
</style>
