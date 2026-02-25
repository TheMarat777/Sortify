<template>
  <main class="det">
    <div class="det__container">

      <!-- ───── Back link ───── -->
      <NuxtLink to="/dashboard" class="det__back">← All Projects</NuxtLink>

      <!-- ───── Hero Header ───── -->
      <section class="det__hero" :style="{ '--accent': project.accent }">
        <div class="det__hero-inner">
          <span class="det__status" :class="'det__status--' + project.status">
            {{ project.status }}
          </span>
          <h1 class="det__title">{{ project.name }}</h1>
          <p class="det__building">{{ project.building }}</p>
          <div class="det__meta-row">
            <span class="det__meta-chip">📍 {{ project.location }}</span>
            <span class="det__meta-chip">🗓️ Started {{ project.started }}</span>
            <span class="det__meta-chip">👷 {{ project.contractor }}</span>
          </div>
        </div>
      </section>

      <!-- ───── Stat Cards ───── -->
      <section class="det__stats">
        <article
          v-for="card in statCards"
          :key="card.key"
          class="det__card"
          :style="{ '--card-accent': card.color }"
        >
          <div class="det__card-icon-wrap">
            <span class="det__card-icon">{{ card.icon }}</span>
          </div>
          <div class="det__card-info">
            <span class="det__card-label">{{ card.label }}</span>
            <span class="det__card-value">{{ formatNumber(card.value) }}<small> {{ card.unit }}</small></span>
          </div>
          <div class="det__card-bar">
            <div class="det__card-bar-fill" :style="{ width: barPercent(card.value) + '%' }" />
          </div>
        </article>
      </section>

      <!-- ───── Two-column: Map + Info ───── -->
      <div class="det__two-col">

        <!-- Map Section -->
        <section class="det__map-card">
          <div class="det__map-card-header">
            <div class="det__map-card-icon">📍</div>
            <div>
              <h2 class="det__section-title">Project Location</h2>
              <p class="det__section-sub">Live site coordinates on OpenStreetMap</p>
            </div>
          </div>
          <div class="det__map-wrap">
            <ClientOnly>
              <iframe
                :src="mapUrl"
                class="det__map-iframe"
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
                allowfullscreen
              />
              <template #fallback>
                <div class="det__map-loading">
                  <span class="det__map-spinner" />
                  Loading map…
                </div>
              </template>
            </ClientOnly>
          </div>
          <div class="det__map-footer">
            <span class="det__map-pin">📌</span>
            <div class="det__map-footer-text">
              <span class="det__map-address">{{ project.address }}</span>
              <span class="det__map-coords">{{ project.lat.toFixed(4) }}°N, {{ project.lng.toFixed(4) }}°E</span>
            </div>
            <a
              :href="'https://www.openstreetmap.org/?mlat=' + project.lat + '&mlon=' + project.lng + '#map=16/' + project.lat + '/' + project.lng"
              target="_blank"
              rel="noopener"
              class="det__map-open"
            >
              Open in Map ↗
            </a>
          </div>
        </section>

        <!-- Project Details -->
        <section class="det__info-card">
          <div class="det__info-card-header">
            <div class="det__info-card-icon">🏢</div>
            <div>
              <h2 class="det__section-title">Project Details</h2>
              <p class="det__section-sub">Key specifications &amp; targets</p>
            </div>
          </div>
          <dl class="det__details">
            <div v-for="(item, idx) in detailRows" :key="idx" class="det__detail-row">
              <dt>
                <span class="det__detail-dot" :style="{ background: item.dot }" />
                {{ item.label }}
              </dt>
              <dd :class="{ 'det__highlight': item.highlight }">{{ item.value }}</dd>
            </div>
          </dl>
          <div class="det__reuse-banner">
            <div class="det__reuse-banner-inner">
              <span class="det__reuse-icon">♻️</span>
              <div>
                <span class="det__reuse-label">Reuse Target</span>
                <span class="det__reuse-value">{{ project.reuseTarget }}</span>
              </div>
            </div>
            <div class="det__reuse-bar">
              <div class="det__reuse-bar-fill" :style="{ width: reusePercent + '%' }" />
            </div>
          </div>
        </section>
      </div>

      <!-- ───── Recent Registrations ───── -->
      <section class="det__recent">
        <div class="det__recent-header">
          <div class="det__recent-header-left">
            <div class="det__recent-icon">📦</div>
            <div>
              <h2 class="det__section-title">Recent Registrations</h2>
              <p class="det__section-sub">{{ project.materials.length }} materials logged</p>
            </div>
          </div>
          <div class="det__recent-legend">
            <span class="det__legend-item"><span class="det__legend-dot det__legend-dot--available" /> Available</span>
            <span class="det__legend-item"><span class="det__legend-dot det__legend-dot--reserved" /> Reserved</span>
            <span class="det__legend-item"><span class="det__legend-dot det__legend-dot--pending" /> Pending</span>
            <span class="det__legend-item"><span class="det__legend-dot det__legend-dot--sold" /> Sold</span>
          </div>
        </div>
        <div class="det__table-wrap">
          <table class="det__table">
            <thead>
              <tr>
                <th>#</th>
                <th>Material</th>
                <th>Quantity</th>
                <th>Status</th>
                <th>Date</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(entry, i) in project.materials" :key="i">
                <td class="det__table-num">{{ i + 1 }}</td>
                <td class="det__table-name">
                  <span class="det__table-name-dot" :class="'det__table-name-dot--' + entry.status.toLowerCase()" />
                  {{ entry.name }}
                </td>
                <td class="det__table-qty">{{ entry.quantity }}</td>
                <td>
                  <span class="det__table-status" :class="'det__table-status--' + entry.status.toLowerCase()">
                    {{ entry.status }}
                  </span>
                </td>
                <td class="det__table-date">{{ entry.date }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div v-if="project.materials.length === 0" class="det__table-empty">
          <span>🚧</span>
          <p>No materials registered yet — project is still in planning phase.</p>
        </div>
      </section>

    </div>
  </main>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

interface MaterialEntry {
  name: string
  quantity: string
  status: string
  date: string
}

interface ProjectDetail {
  id: number
  name: string
  location: string
  building: string
  address: string
  buildingType: string
  yearBuilt: string
  floorArea: string
  contractor: string
  estCompletion: string
  reuseTarget: string
  started: string
  status: 'active' | 'completed' | 'planned'
  accent: string
  lat: number
  lng: number
  stats: { concrete: number; wood: number; metal: number; reusable: number }
  materials: MaterialEntry[]
}

const projectsDB: Record<number, ProjectDetail> = {
  1: {
    id: 1,
    name: 'Aarhus University Hospital Wing B',
    location: 'Aarhus',
    building: 'Demolition of the 1970s radiology wing — 4 stories, steel-frame structure with concrete facade panels.',
    address: 'Palle Juul-Jensens Blvd 99, 8200 Aarhus N',
    buildingType: 'Hospital / Medical',
    yearBuilt: '1974',
    floorArea: '6,200 m²',
    contractor: 'NCC Denmark A/S',
    estCompletion: 'Aug 2026',
    reuseTarget: '70% of materials',
    started: 'Feb 2026',
    status: 'active',
    accent: '#2f7a3e',
    lat: 56.1710,
    lng: 10.1930,
    stats: { concrete: 12_000, wood: 3_200, metal: 950, reusable: 640 },
    materials: [
      { name: 'Concrete Facade Panels', quantity: '4,800 kg', status: 'Available', date: '24 Feb' },
      { name: 'Steel I-Beams', quantity: '1,200 kg', status: 'Reserved', date: '22 Feb' },
      { name: 'Wood Ceiling Frames', quantity: '320 pcs', status: 'Available', date: '20 Feb' },
      { name: 'Copper Wiring', quantity: '180 m', status: 'Pending', date: '18 Feb' },
      { name: 'Window Aluminium Frames', quantity: '96 pcs', status: 'Available', date: '17 Feb' },
      { name: 'Terrazzo Floor Tiles', quantity: '640 kg', status: 'Sold', date: '15 Feb' },
    ],
  },
  2: {
    id: 2,
    name: 'Carlsberg Byen Warehouse 7',
    location: 'Copenhagen',
    building: 'Selective strip-out of a 1920s brick warehouse in the Carlsberg district for adaptive reuse conversion.',
    address: 'Ny Carlsberg Vej 80, 1799 København V',
    buildingType: 'Industrial / Warehouse',
    yearBuilt: '1923',
    floorArea: '9,400 m²',
    contractor: 'MT Højgaard A/S',
    estCompletion: 'Oct 2026',
    reuseTarget: '85% of materials',
    started: 'Jan 2026',
    status: 'active',
    accent: '#92400e',
    lat: 55.6631,
    lng: 12.5328,
    stats: { concrete: 8_500, wood: 6_800, metal: 4_200, reusable: 4_800 },
    materials: [
      { name: 'Red Hand-Made Bricks', quantity: '12,400 pcs', status: 'Available', date: '24 Feb' },
      { name: 'Oak Roof Trusses', quantity: '2,100 kg', status: 'Available', date: '23 Feb' },
      { name: 'Cast-Iron Columns', quantity: '18 pcs', status: 'Reserved', date: '21 Feb' },
      { name: 'Timber Floorboards', quantity: '340 m²', status: 'Sold', date: '19 Feb' },
      { name: 'Original Steel Windows', quantity: '48 pcs', status: 'Available', date: '17 Feb' },
    ],
  },
  3: {
    id: 3,
    name: 'Odense Harbour Silo Complex',
    location: 'Odense',
    building: 'Demolition of three 1960s grain silos at the inner harbour — reinforced concrete, 40 m tall.',
    address: 'Havnegade 22, 5000 Odense C',
    buildingType: 'Industrial / Silo',
    yearBuilt: '1962',
    floorArea: '3,800 m²',
    contractor: 'Per Aarsleff A/S',
    estCompletion: 'Dec 2026',
    reuseTarget: '45% of materials',
    started: 'Mar 2026',
    status: 'planned',
    accent: '#6b7280',
    lat: 55.4038,
    lng: 10.4024,
    stats: { concrete: 0, wood: 0, metal: 0, reusable: 0 },
    materials: [],
  },
  4: {
    id: 4,
    name: 'Aalborg Cement Factory East',
    location: 'Aalborg',
    building: 'Partial teardown of the eastern kiln building — heavy steel beams, refractory bricks, copper wiring.',
    address: 'Rørdalsvej 44, 9220 Aalborg Øst',
    buildingType: 'Industrial / Factory',
    yearBuilt: '1958',
    floorArea: '11,600 m²',
    contractor: 'Aarsleff A/S',
    estCompletion: 'Jun 2026',
    reuseTarget: '60% of materials',
    started: 'Dec 2025',
    status: 'active',
    accent: '#374151',
    lat: 57.0488,
    lng: 9.9217,
    stats: { concrete: 18_000, wood: 1_500, metal: 8_200, reusable: 3_800 },
    materials: [
      { name: 'Refractory Bricks', quantity: '6,800 kg', status: 'Available', date: '23 Feb' },
      { name: 'Heavy Steel Beams', quantity: '5,400 kg', status: 'Available', date: '22 Feb' },
      { name: 'Copper Wire Bundles', quantity: '920 m', status: 'Pending', date: '20 Feb' },
      { name: 'Reinforced Concrete Slabs', quantity: '8,200 kg', status: 'Available', date: '18 Feb' },
      { name: 'Industrial Grating', quantity: '240 m²', status: 'Reserved', date: '16 Feb' },
      { name: 'Steel Pipe Sections', quantity: '1,400 m', status: 'Sold', date: '14 Feb' },
      { name: 'Cast Aluminium Fixtures', quantity: '320 pcs', status: 'Available', date: '12 Feb' },
    ],
  },
  5: {
    id: 5,
    name: 'Frederiksberg School Renovation',
    location: 'Frederiksberg',
    building: 'Interior gutting of a 1950s public school — timber roof trusses, terrazzo floors, original oak doors.',
    address: 'Godthåbsvej 35, 2000 Frederiksberg',
    buildingType: 'Education / School',
    yearBuilt: '1953',
    floorArea: '4,100 m²',
    contractor: 'Enemærke & Petersen A/S',
    estCompletion: 'Completed',
    reuseTarget: '75% of materials',
    started: 'Nov 2025',
    status: 'completed',
    accent: '#7c3aed',
    lat: 55.6794,
    lng: 12.5317,
    stats: { concrete: 2_200, wood: 3_400, metal: 800, reusable: 2_000 },
    materials: [
      { name: 'Oak Panel Doors', quantity: '64 pcs', status: 'Sold', date: '10 Jan' },
      { name: 'Timber Roof Trusses', quantity: '1,800 kg', status: 'Sold', date: '08 Jan' },
      { name: 'Terrazzo Floor Pieces', quantity: '280 m²', status: 'Sold', date: '05 Jan' },
      { name: 'Cast-Iron Radiators', quantity: '42 pcs', status: 'Sold', date: '02 Jan' },
      { name: 'Original Brass Handles', quantity: '180 pcs', status: 'Available', date: '28 Dec' },
    ],
  },
  6: {
    id: 6,
    name: 'Roskilde Viking Museum Hall',
    location: 'Roskilde',
    building: 'Teardown of the 1969 exhibition wing — exposed aggregate concrete, laminated timber arches, zinc cladding.',
    address: 'Vindeboder 12, 4000 Roskilde',
    buildingType: 'Cultural / Museum',
    yearBuilt: '1969',
    floorArea: '3,600 m²',
    contractor: 'Hoffmann A/S',
    estCompletion: 'Sep 2026',
    reuseTarget: '65% of materials',
    started: 'Jan 2026',
    status: 'active',
    accent: '#0e7490',
    lat: 55.6508,
    lng: 12.0813,
    stats: { concrete: 5_400, wood: 2_800, metal: 1_600, reusable: 1_450 },
    materials: [
      { name: 'Laminated Timber Arches', quantity: '1,400 kg', status: 'Available', date: '24 Feb' },
      { name: 'Exposed Aggregate Panels', quantity: '3,200 kg', status: 'Available', date: '22 Feb' },
      { name: 'Zinc Roof Sheets', quantity: '680 m²', status: 'Reserved', date: '20 Feb' },
      { name: 'Display Glass Panels', quantity: '48 pcs', status: 'Pending', date: '18 Feb' },
      { name: 'Steel Roof Trusses', quantity: '960 kg', status: 'Available', date: '16 Feb' },
      { name: 'Concrete Floor Slabs', quantity: '2,200 kg', status: 'Available', date: '14 Feb' },
      { name: 'Oak Exhibit Platforms', quantity: '36 pcs', status: 'Sold', date: '12 Feb' },
    ],
  },
}

/* ──── Resolve current project ──── */
const projectId = Number(route.params.id)
const project: ProjectDetail = projectsDB[projectId] ?? projectsDB[1]!

const statCards = [
  { key: 'concrete', label: 'Concrete',       value: project.stats.concrete, unit: 'kg',    icon: '🧱', color: '#6b7280' },
  { key: 'wood',     label: 'Wood',           value: project.stats.wood,     unit: 'kg',    icon: '🪵', color: '#92400e' },
  { key: 'metal',    label: 'Metal',          value: project.stats.metal,    unit: 'kg',    icon: '⚙️', color: '#374151' },
  { key: 'reusable', label: 'Reusable Items', value: project.stats.reusable, unit: 'items', icon: '♻️', color: '#2f7a3e' },
]
const maxStat = Math.max(...statCards.map((c) => c.value), 1)

function formatNumber(n: number) { return n.toLocaleString('en-DK') }
function barPercent(v: number) { return Math.round((v / maxStat) * 100) }

/* ──── Detail rows for Project Details card ──── */
const detailRows = [
  { label: 'Building type', value: project.buildingType, dot: '#6b7280', highlight: false },
  { label: 'Year built', value: project.yearBuilt, dot: '#92400e', highlight: false },
  { label: 'Floor area', value: project.floorArea, dot: '#2f7a3e', highlight: false },
  { label: 'Contractor', value: project.contractor, dot: '#374151', highlight: false },
  { label: 'Est. completion', value: project.estCompletion, dot: '#7c3aed', highlight: false },
]

/* ──── Parse reuse target percentage for progress bar ──── */
const reusePercent = parseInt(project.reuseTarget) || 0

/* ──── OpenStreetMap embed URL ──── */
const mapUrl = computed(() => {
  const bbox = `${project.lng - 0.012},${project.lat - 0.008},${project.lng + 0.012},${project.lat + 0.008}`
  const marker = `${project.lat},${project.lng}`
  return `https://www.openstreetmap.org/export/embed.html?bbox=${bbox}&layer=mapnik&marker=${marker}`
})
</script>

<style scoped>
/* ──────── Page ──────── */
.det {
  flex: 1;
  padding: 32px 24px 80px;
  background: linear-gradient(175deg, #f6f7f3 0%, #eef0e8 100%);
}
.det__container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 28px;
}

/* ──── Back ──── */
.det__back {
  font-size: 0.88rem;
  font-weight: 600;
  color: var(--color-green, #2f7a3e);
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 4px;
  transition: opacity 0.15s;
}
.det__back:hover { opacity: 0.7; }

/* ──── Hero ──── */
.det__hero {
  background: linear-gradient(135deg, var(--accent, #2f7a3e) 0%, color-mix(in srgb, var(--accent, #2f7a3e) 60%, #000) 100%);
  border-radius: 18px;
  padding: 36px 32px;
  color: #fff;
  position: relative;
  overflow: hidden;
}
.det__hero::after {
  content: '';
  position: absolute;
  top: -40%;
  right: -10%;
  width: 300px;
  height: 300px;
  border-radius: 50%;
  background: rgba(255,255,255,0.06);
}
.det__hero-inner { position: relative; z-index: 1; }
.det__status {
  display: inline-block;
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  padding: 4px 12px;
  border-radius: 12px;
  margin-bottom: 12px;
}
.det__status--active { background: rgba(255,255,255,0.2); color: #d1fae5; }
.det__status--completed { background: rgba(255,255,255,0.2); color: #bfdbfe; }
.det__status--planned { background: rgba(255,255,255,0.2); color: #e5e7eb; }
.det__title {
  font-size: 2.2rem;
  font-weight: 800;
  margin: 0 0 8px;
  letter-spacing: -0.02em;
}
.det__building {
  font-size: 0.95rem;
  margin: 0 0 16px;
  opacity: 0.85;
  line-height: 1.5;
  max-width: 700px;
}
.det__meta-row { display: flex; gap: 10px; flex-wrap: wrap; }
.det__meta-chip {
  background: rgba(255,255,255,0.15);
  padding: 5px 14px;
  border-radius: 20px;
  font-size: 0.82rem;
  backdrop-filter: blur(4px);
}

/* ──── Stat Cards ──── */
.det__stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
}
.det__card {
  background: #fff;
  border-radius: 14px;
  padding: 18px;
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: center;
  box-shadow: 0 2px 12px rgba(0,0,0,0.06);
  transition: transform 0.2s, box-shadow 0.2s;
  position: relative;
  overflow: hidden;
}
.det__card::before {
  content: '';
  position: absolute;
  left: 0; top: 0; bottom: 0;
  width: 4px;
  background: var(--card-accent, var(--color-green));
}
.det__card:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 24px rgba(0,0,0,0.1);
}
.det__card-icon-wrap {
  width: 44px; height: 44px;
  border-radius: 12px;
  background: color-mix(in srgb, var(--card-accent, #2f7a3e) 12%, transparent);
  display: flex; align-items: center; justify-content: center;
  font-size: 1.3rem;
}
.det__card-info { flex: 1; min-width: 0; }
.det__card-label {
  display: block;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #888;
  font-weight: 600;
}
.det__card-value {
  font-size: 1.5rem;
  font-weight: 800;
  color: #1a1a1a;
  line-height: 1.2;
}
.det__card-value small {
  font-size: 0.65rem;
  font-weight: 600;
  color: #999;
}
.det__card-bar {
  width: 100%;
  height: 4px;
  border-radius: 2px;
  background: #eee;
}
.det__card-bar-fill {
  height: 100%;
  border-radius: 2px;
  background: var(--card-accent, var(--color-green));
  transition: width 0.6s cubic-bezier(.4,0,.2,1);
}

/* ──── Section shared ──── */
.det__section-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: #1a1a1a;
  margin: 0;
  line-height: 1.3;
}
.det__section-sub {
  font-size: 0.78rem;
  color: #999;
  margin: 2px 0 0;
  font-weight: 500;
}

/* ═══════════════════════════════════════════
   🔥 BEAST MODE — Two-Column Map + Info
   ═══════════════════════════════════════════ */
.det__two-col {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 20px;
}

/* ── Map Card ── */
.det__map-card {
  background: #fff;
  border-radius: 18px;
  padding: 0;
  box-shadow: 0 4px 24px rgba(0,0,0,0.07);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: box-shadow 0.3s;
}
.det__map-card:hover {
  box-shadow: 0 8px 40px rgba(0,0,0,0.12);
}
.det__map-card-header {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 20px 24px 0;
}
.det__map-card-icon {
  width: 42px; height: 42px;
  border-radius: 12px;
  background: linear-gradient(135deg, #e6f4ea, #d4edda);
  display: flex; align-items: center; justify-content: center;
  font-size: 1.2rem;
  flex-shrink: 0;
}
.det__map-wrap {
  margin: 16px 16px 0;
  border-radius: 14px;
  overflow: hidden;
  height: 300px;
  background: #e9ebe5;
  position: relative;
  border: 2px solid #f0f0ec;
}
.det__map-iframe {
  width: 100%; height: 100%;
  border: none;
  display: block;
}
.det__map-loading {
  display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 10px;
  height: 100%; color: #999; font-size: 0.88rem;
}
.det__map-spinner {
  width: 28px; height: 28px;
  border: 3px solid #e0e0e0;
  border-top-color: var(--color-green, #2f7a3e);
  border-radius: 50%;
  animation: spin 0.7s linear infinite;
}
@keyframes spin { to { transform: rotate(360deg); } }

.det__map-footer {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 14px 24px 18px;
  border-top: 1px solid #f4f4f0;
  margin-top: auto;
}
.det__map-pin { font-size: 1.1rem; }
.det__map-footer-text { flex: 1; min-width: 0; }
.det__map-address {
  display: block;
  font-size: 0.88rem;
  font-weight: 600;
  color: #1a1a1a;
  margin: 0;
}
.det__map-coords {
  display: block;
  font-size: 0.72rem;
  color: #aaa;
  margin-top: 1px;
  font-family: 'SF Mono', SFMono-Regular, Consolas, monospace;
}
.det__map-open {
  font-size: 0.78rem;
  font-weight: 600;
  color: var(--color-green, #2f7a3e);
  text-decoration: none;
  padding: 6px 14px;
  border-radius: 8px;
  border: 1px solid rgba(47,122,62,0.2);
  background: rgba(47,122,62,0.06);
  white-space: nowrap;
  transition: all 0.2s;
}
.det__map-open:hover {
  background: rgba(47,122,62,0.14);
  border-color: rgba(47,122,62,0.4);
}

/* ── Info Card ── */
.det__info-card {
  background: #fff;
  border-radius: 18px;
  padding: 0;
  box-shadow: 0 4px 24px rgba(0,0,0,0.07);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: box-shadow 0.3s;
}
.det__info-card:hover {
  box-shadow: 0 8px 40px rgba(0,0,0,0.12);
}
.det__info-card-header {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 20px 24px 16px;
}
.det__info-card-icon {
  width: 42px; height: 42px;
  border-radius: 12px;
  background: linear-gradient(135deg, #e8f0fe, #d6e4ff);
  display: flex; align-items: center; justify-content: center;
  font-size: 1.2rem;
  flex-shrink: 0;
}
.det__details {
  margin: 0;
  padding: 0 24px;
  flex: 1;
}
.det__detail-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 0;
  border-bottom: 1px solid #f5f5f2;
  transition: background 0.15s;
}
.det__detail-row:hover {
  background: #fafbf8;
  margin: 0 -24px;
  padding-left: 24px;
  padding-right: 24px;
}
.det__detail-row:last-child { border-bottom: none; }
.det__detail-row dt {
  font-size: 0.84rem;
  color: #888;
  font-weight: 500;
  display: flex;
  align-items: center;
  gap: 8px;
}
.det__detail-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  display: inline-block;
  flex-shrink: 0;
}
.det__detail-row dd {
  margin: 0;
  font-size: 0.88rem;
  font-weight: 600;
  color: #1a1a1a;
  text-align: right;
}
.det__highlight {
  color: var(--color-green, #2f7a3e) !important;
}

/* ── Reuse Target Banner ── */
.det__reuse-banner {
  margin-top: auto;
  padding: 16px 24px 20px;
  background: linear-gradient(135deg, rgba(47,122,62,0.06), rgba(47,122,62,0.02));
  border-top: 1px solid #e6f4ea;
}
.det__reuse-banner-inner {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}
.det__reuse-icon { font-size: 1.4rem; }
.det__reuse-label {
  display: block;
  font-size: 0.7rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  font-weight: 600;
  color: #888;
}
.det__reuse-value {
  display: block;
  font-size: 1.1rem;
  font-weight: 800;
  color: var(--color-green, #2f7a3e);
  line-height: 1.2;
}
.det__reuse-bar {
  height: 6px;
  border-radius: 3px;
  background: rgba(47,122,62,0.12);
  overflow: hidden;
}
.det__reuse-bar-fill {
  height: 100%;
  border-radius: 3px;
  background: linear-gradient(90deg, #2f7a3e, #4caf50);
  transition: width 0.8s cubic-bezier(.4,0,.2,1);
}

/* ═══════════════════════════════════════════
   🔥 BEAST MODE — Recent Registrations
   ═══════════════════════════════════════════ */
.det__recent {
  background: #fff;
  border-radius: 18px;
  padding: 0;
  box-shadow: 0 4px 24px rgba(0,0,0,0.07);
  overflow: hidden;
  transition: box-shadow 0.3s;
}
.det__recent:hover {
  box-shadow: 0 8px 40px rgba(0,0,0,0.12);
}
.det__recent-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 24px 16px;
  flex-wrap: wrap;
  gap: 12px;
}
.det__recent-header-left {
  display: flex;
  align-items: center;
  gap: 12px;
}
.det__recent-icon {
  width: 42px; height: 42px;
  border-radius: 12px;
  background: linear-gradient(135deg, #fef3cd, #fde68a);
  display: flex; align-items: center; justify-content: center;
  font-size: 1.2rem;
  flex-shrink: 0;
}
.det__recent-legend {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}
.det__legend-item {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 0.72rem;
  color: #999;
  font-weight: 500;
}
.det__legend-dot {
  width: 8px; height: 8px;
  border-radius: 50%;
  display: inline-block;
}
.det__legend-dot--available { background: #1e7e34; }
.det__legend-dot--reserved { background: #1a56db; }
.det__legend-dot--pending { background: #856404; }
.det__legend-dot--sold { background: #c0392b; }

.det__table-wrap {
  overflow-x: auto;
  padding: 0 8px;
}
.det__table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
.det__table thead th {
  text-align: left;
  font-size: 0.7rem;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #aaa;
  font-weight: 600;
  padding: 10px 16px;
  border-bottom: 2px solid #f0f0ec;
  background: #fafbf8;
}
.det__table tbody tr {
  transition: all 0.18s;
}
.det__table tbody tr:hover {
  background: linear-gradient(90deg, rgba(47,122,62,0.03), transparent);
}
.det__table td {
  padding: 14px 16px;
  border-bottom: 1px solid #f5f5f2;
  color: #333;
  vertical-align: middle;
}
.det__table tbody tr:last-child td {
  border-bottom: none;
}
.det__table-num {
  font-size: 0.72rem;
  color: #ccc;
  font-weight: 700;
  font-family: 'SF Mono', SFMono-Regular, Consolas, monospace;
  width: 32px;
}
.det__table-name {
  font-weight: 600;
  color: #1a1a1a;
  display: flex;
  align-items: center;
  gap: 8px;
}
.det__table-name-dot {
  width: 8px; height: 8px;
  border-radius: 50%;
  display: inline-block;
  flex-shrink: 0;
}
.det__table-name-dot--available { background: #1e7e34; }
.det__table-name-dot--reserved { background: #1a56db; }
.det__table-name-dot--pending { background: #856404; }
.det__table-name-dot--sold { background: #c0392b; }
.det__table-qty {
  font-family: 'SF Mono', SFMono-Regular, Consolas, monospace;
  font-size: 0.84rem;
  color: #555;
}
.det__table-date {
  color: #bbb;
  font-size: 0.8rem;
  white-space: nowrap;
}
.det__table-status {
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  padding: 4px 12px;
  border-radius: 20px;
  display: inline-block;
}
.det__table-status--available { background: #e6f4ea; color: #1e7e34; }
.det__table-status--sold { background: #fce4e4; color: #c0392b; }
.det__table-status--pending { background: #fef3cd; color: #856404; }
.det__table-status--reserved { background: #e8f0fe; color: #1a56db; }

.det__table-empty {
  text-align: center;
  padding: 40px 24px;
  color: #bbb;
}
.det__table-empty span { font-size: 2rem; display: block; margin-bottom: 8px; }
.det__table-empty p { margin: 0; font-size: 0.9rem; }

/* ──── Responsive ──── */
@media (max-width: 900px) {
  .det__stats { grid-template-columns: repeat(2, 1fr); }
  .det__two-col { grid-template-columns: 1fr; }
  .det__recent-header { flex-direction: column; align-items: flex-start; }
}
@media (max-width: 600px) {
  .det { padding: 16px 16px 48px; }
  .det__title { font-size: 1.5rem; }
  .det__stats { grid-template-columns: 1fr; }
  .det__hero { padding: 24px 20px; }
  .det__map-wrap { height: 220px; margin: 12px 12px 0; }
  .det__table td { padding: 10px 10px; }
  .det__recent-legend { display: none; }
}
</style>
