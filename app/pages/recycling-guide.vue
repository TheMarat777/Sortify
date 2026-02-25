<template>
  <main class="rg">
    <div class="rg__container">

      <!-- ───── Hero ───── -->
      <section class="rg__hero">
        <span class="rg__badge">♻️ Sustainability Knowledge</span>
        <h1 class="rg__title">Recycling Guide</h1>
        <p class="rg__subtitle">
          Your comprehensive guide to sorting, recycling and reusing construction
          materials — reducing waste and building a circular economy in Denmark.
        </p>
      </section>

      <!-- ───── Waste Hierarchy Pyramid ───── -->
      <section class="rg__pyramid-section">
        <h2 class="rg__section-title">
          <span class="rg__section-icon">🔺</span>
          The Waste Hierarchy
        </h2>
        <p class="rg__section-desc">
          The EU Waste Framework Directive prioritises actions from most to least
          preferred. Sortify focuses on the top three tiers.
        </p>
        <div class="rg__pyramid">
          <div
            v-for="(tier, i) in hierarchy"
            :key="tier.label"
            class="rg__tier"
            :class="'rg__tier--' + (i + 1)"
            :style="{ '--tier-color': tier.color }"
          >
            <span class="rg__tier-rank">{{ i + 1 }}</span>
            <div>
              <strong class="rg__tier-label">{{ tier.label }}</strong>
              <p class="rg__tier-desc">{{ tier.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Material Categories ───── -->
      <section class="rg__categories">
        <h2 class="rg__section-title">
          <span class="rg__section-icon"></span>
          Material Categories
        </h2>
        <p class="rg__section-desc">
          Common construction materials and how to handle them responsibly.
        </p>
        <div class="rg__cat-grid">
          <div
            v-for="cat in categories"
            :key="cat.name"
            class="rg__cat-card"
            :style="{ '--cat-accent': cat.accent }"
          >
            <h3 class="rg__cat-name">{{ cat.name }}</h3>
            <p class="rg__cat-desc">{{ cat.desc }}</p>
            <div class="rg__cat-tags">
              <span v-for="t in cat.tags" :key="t" class="rg__cat-tag">{{ t }}</span>
            </div>
            <div class="rg__cat-rate">
              <div class="rg__cat-rate-bar">
                <div class="rg__cat-rate-fill" :style="{ width: cat.rate }" />
              </div>
              <span class="rg__cat-rate-label">{{ cat.rate }} recyclable</span>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Best Practices (full-bleed brown layer) ───── -->
      <section class="rg__tips-section">
        <h2 class="rg__section-title">
          <span class="rg__section-icon"></span>
          Best Practices
        </h2>
        <div class="rg__tips-grid">
          <div v-for="tip in tips" :key="tip.title" class="rg__tip-card">
            <span class="rg__tip-num">{{ tip.num }}</span>
            <div>
              <h3 class="rg__tip-title">{{ tip.title }}</h3>
              <p class="rg__tip-desc">{{ tip.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- ───── Danish Regulations ───── -->
      <section class="rg__regs">
        <h2 class="rg__section-title">
          <span class="rg__section-icon"></span>
          Danish Regulations
        </h2>
        <p class="rg__section-desc">
          Key regulatory frameworks that guide construction waste management in Denmark.
        </p>
        <div class="rg__regs-grid">
          <div v-for="reg in regulations" :key="reg.title" class="rg__reg-card">
            <div class="rg__reg-badge">{{ reg.type }}</div>
            <h3 class="rg__reg-title">{{ reg.title }}</h3>
            <p class="rg__reg-desc">{{ reg.desc }}</p>
          </div>
        </div>
      </section>

      <!-- ───── CTA Banner ───── -->
      <section class="rg__cta-banner">
        <div class="rg__cta-inner">
          <h2 class="rg__cta-title">Ready to make a difference?</h2>
          <p class="rg__cta-desc">
            Start listing leftover materials from your demolition projects today.
          </p>
          <div class="rg__cta-actions">
            <NuxtLink to="/add-material" class="rg__cta-btn rg__cta-btn--primary">
              Add Material →
            </NuxtLink>
            <NuxtLink to="/marketplace" class="rg__cta-btn rg__cta-btn--secondary">
              Browse Marketplace
            </NuxtLink>
          </div>
        </div>
      </section>

    </div>
  </main>
</template>

<script setup lang="ts">
const hierarchy = [
  { label: 'Prevention', desc: 'Reduce waste generation through better design and planning.', color: '#16a34a' },
  { label: 'Reuse', desc: 'Extend material lifespan by reusing in new construction projects.', color: '#22c55e' },
  { label: 'Recycling', desc: 'Process materials into new raw inputs for manufacturing.', color: '#86efac' },
  { label: 'Recovery', desc: 'Extract energy from waste that cannot be recycled.', color: '#fbbf24' },
  { label: 'Disposal', desc: 'Landfill only as an absolute last resort.', color: '#ef4444' },
]

const categories = [
  {
    name: 'Concrete & Masonry', accent: '#6b7280',
    desc: 'Crushed concrete can be reused as aggregate for road base and new concrete mixes.',
    tags: ['Concrete', 'Bricks', 'Blocks', 'Mortar'],
    rate: '85%',
  },
  {
    name: 'Timber & Wood', accent: '#92400e',
    desc: 'Untreated timber is ideal for reuse in framing, furniture and biomass energy.',
    tags: ['Beams', 'Planks', 'Plywood', 'Trusses'],
    rate: '72%',
  },
  {
    name: 'Metals', accent: '#374151',
    desc: 'Steel, copper and aluminium have extremely high recycling rates and retain material quality.',
    tags: ['Steel I-beams', 'Rebar', 'Copper pipe', 'Aluminium'],
    rate: '95%',
  },
  {
    name: 'Glass & Glazing', accent: '#0e7490',
    desc: 'Flat glass from windows can be recycled into new glass products or insulation materials.',
    tags: ['Window panes', 'Glass blocks', 'Mirrors'],
    rate: '60%',
  },
  {
    name: 'Insulation', accent: '#7c3aed',
    desc: 'Mineral wool and fiberglass can be recycled. Bio-based insulation is compostable.',
    tags: ['Glass wool', 'Rock wool', 'EPS', 'Hemp'],
    rate: '45%',
  },
  {
    name: 'Roofing & Cladding', accent: '#b45309',
    desc: 'Tiles, zinc and slate are highly durable and perfect candidates for direct reuse.',
    tags: ['Clay tiles', 'Zinc sheets', 'Slate', 'Bitumen'],
    rate: '68%',
  },
]

const tips = [
  { num: '01', title: 'Pre-demolition audit', desc: 'Conduct a material inventory before any demolition work begins. Identify reusable and hazardous materials early.' },
  { num: '02', title: 'Selective demolition', desc: 'Deconstruct rather than demolish. Careful disassembly preserves material integrity and maximises reuse potential.' },
  { num: '03', title: 'On-site sorting', desc: 'Set up clearly labelled sorting stations. Separate concrete, timber, metals and hazardous waste at the source.' },
  { num: '04', title: 'Digital registration', desc: 'Use Sortify to register materials as they are identified. The sooner they are listed, the more likely they find a buyer.' },
  { num: '05', title: 'Quality documentation', desc: 'Photograph materials, note dimensions and condition. Detailed listings attract more interest from buyers.' },
  { num: '06', title: 'Transport planning', desc: 'Coordinate pickup logistics early. Materials lose value if they block site access or require emergency removal.' },
]

const regulations = [
  {
    type: 'Directive',
    title: 'EU Waste Framework (2008/98/EC)',
    desc: 'Mandates 70% recovery of construction and demolition waste by weight across all EU member states.',
  },
  {
    type: 'National',
    title: 'Danish Environmental Protection Act',
    desc: 'Requires environmental screening and waste management plans for demolition projects above 10 tonnes.',
  },
  {
    type: 'Standard',
    title: 'DS/EN 15804 EPD',
    desc: 'Environmental Product Declarations provide lifecycle data that supports informed material reuse decisions.',
  },
  {
    type: 'Municipal',
    title: 'Kommunal affaldsplan',
    desc: 'Each Danish municipality maintains a waste plan with specific sorting and reporting obligations for construction sites.',
  },
]
</script>

<style scoped>
.rg {
  flex: 1;
  padding: 40px 24px 0;
  background: linear-gradient(175deg, #f6f7f3 0%, #eef0e8 100%);
}
.rg__container {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 56px;
  padding-bottom: 0;
}

/* remove gap after last child so CTA sits flush with footer */
.rg__container > :last-child {
  margin-bottom: -56px;
}

/* ──── Hero ──── */
.rg__hero { max-width: 680px; }
.rg__badge {
  display: inline-block;
  background: rgba(47,122,62,0.1);
  color: var(--color-green, #2f7a3e);
  font-size: 0.82rem;
  font-weight: 700;
  padding: 4px 14px;
  border-radius: 20px;
  margin-bottom: 10px;
}
.rg__title {
  font-size: 2.2rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0;
  letter-spacing: -0.02em;
}
.rg__subtitle {
  margin: 10px 0 0;
  font-size: 1.05rem;
  color: #555;
  line-height: 1.6;
}

/* ──── Section headers ──── */
.rg__section-title {
  font-size: 1.5rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0 0 6px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.rg__section-icon { font-size: 1.3rem; }
.rg__section-desc {
  font-size: 0.95rem;
  color: #666;
  margin: 0 0 24px;
  max-width: 600px;
  line-height: 1.55;
}

/* ──── Waste Hierarchy Pyramid ──── */
.rg__pyramid-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.rg__pyramid {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 640px;
}
.rg__tier {
  display: flex;
  align-items: center;
  gap: 16px;
  background: #fff;
  padding: 16px 20px;
  border-radius: 14px;
  border-left: 5px solid var(--tier-color);
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s, box-shadow 0.2s;
}
.rg__tier:hover {
  transform: translateX(6px);
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
}
.rg__tier--1 { margin-left: 0; }
.rg__tier--2 { margin-left: 24px; }
.rg__tier--3 { margin-left: 48px; }
.rg__tier--4 { margin-left: 72px; }
.rg__tier--5 { margin-left: 96px; }
.rg__tier-rank {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: var(--tier-color);
  color: #fff;
  font-weight: 800;
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
.rg__tier-label { font-size: 1rem; color: #1a1a1a; }
.rg__tier-desc { font-size: 0.84rem; color: #777; margin: 2px 0 0; }

/* ──── Material Categories ──── */
.rg__cat-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.rg__cat-card {
  background: #fff;
  border-radius: 16px;
  padding: 24px 22px 20px;
  box-shadow: 0 2px 14px rgba(0,0,0,0.05);
  border-top: 4px solid var(--cat-accent);
  display: flex;
  flex-direction: column;
  gap: 8px;
  transition: transform 0.2s, box-shadow 0.2s;
}
.rg__cat-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.1);
}
.rg__cat-name { font-size: 1.08rem; font-weight: 700; color: #1a1a1a; margin: 0; }
.rg__cat-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; flex: 1; }
.rg__cat-tags { display: flex; flex-wrap: wrap; gap: 6px; }
.rg__cat-tag {
  font-size: 0.74rem;
  font-weight: 600;
  padding: 3px 10px;
  border-radius: 20px;
  background: #f3f4f1;
  color: #555;
}
.rg__cat-rate { margin-top: 4px; }
.rg__cat-rate-bar {
  height: 6px;
  background: #eef0e8;
  border-radius: 3px;
  overflow: hidden;
}
.rg__cat-rate-fill {
  height: 100%;
  background: var(--cat-accent);
  border-radius: 3px;
  transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}
.rg__cat-rate-label { font-size: 0.76rem; color: #888; margin-top: 4px; display: block; }

/* ──── Best Practices (full-bleed brown layer) ──── */
.rg__tips-section {
  background: #f5efe6;
  padding: 48px 32px;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 32px);
  padding-right: calc(50vw - 50% + 32px);
}
.rg__tips-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}
.rg__tip-card {
  display: flex;
  gap: 16px;
  background: #fff;
  border-radius: 14px;
  padding: 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.rg__tip-card:hover { transform: translateY(-3px); }
.rg__tip-num {
  font-size: 1.6rem;
  font-weight: 900;
  color: var(--color-green, #2f7a3e);
  opacity: 0.35;
  line-height: 1;
  flex-shrink: 0;
}
.rg__tip-title { font-size: 0.98rem; font-weight: 700; color: #1a1a1a; margin: 0 0 4px; }
.rg__tip-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── Regulations ──── */
.rg__regs-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}
.rg__reg-card {
  background: #fff;
  border-radius: 14px;
  padding: 22px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.04);
  transition: transform 0.2s;
}
.rg__reg-card:hover { transform: translateY(-3px); }
.rg__reg-badge {
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
.rg__reg-title { font-size: 1rem; font-weight: 700; color: #1a1a1a; margin: 0 0 6px; }
.rg__reg-desc { font-size: 0.84rem; color: #777; line-height: 1.5; margin: 0; }

/* ──── CTA Banner (full-bleed) ──── */
.rg__cta-banner {
  background: linear-gradient(135deg, var(--color-green-dark, #1f5a2b) 0%, var(--color-green, #2f7a3e) 50%, var(--color-brown, #6b4f32) 100%);
  border-radius: 0;
  padding: 64px 40px 80px;
  text-align: center;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: calc(50vw - 50% + 40px);
  padding-right: calc(50vw - 50% + 40px);
  display: flex;
  align-items: center;
  justify-content: center;
}
.rg__cta-inner { max-width: 520px; margin: 0 auto; }
.rg__cta-title { font-size: 1.6rem; font-weight: 800; color: #fff; margin: 0 0 8px; }
.rg__cta-desc { font-size: 1rem; color: rgba(255,255,255,0.85); margin: 0 0 24px; line-height: 1.5; }
.rg__cta-actions { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
.rg__cta-btn {
  display: inline-block;
  padding: 12px 28px;
  border-radius: 10px;
  font-size: 0.95rem;
  font-weight: 700;
  text-decoration: none;
  transition: transform 0.15s, box-shadow 0.2s;
}
.rg__cta-btn:hover { transform: translateY(-2px); box-shadow: 0 4px 16px rgba(0,0,0,0.2); }
.rg__cta-btn--primary { background: #fff; color: var(--color-green-dark, #1f5a2b); }
.rg__cta-btn--secondary { background: rgba(255,255,255,0.15); color: #fff; border: 1px solid rgba(255,255,255,0.3); }

/* ──── Responsive ──── */
@media (max-width: 900px) {
  .rg__cat-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .rg { padding: 20px 16px 48px; }
  .rg__title { font-size: 1.5rem; }
  .rg__cat-grid,
  .rg__tips-grid,
  .rg__regs-grid { grid-template-columns: 1fr; }
  .rg__tier--2,
  .rg__tier--3,
  .rg__tier--4,
  .rg__tier--5 { margin-left: 0; }
  .rg__cta-banner { padding: 32px 20px; }
}
</style>
