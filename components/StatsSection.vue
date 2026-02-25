<template>
  <section class="stats">
    <!-- subtle floating shapes in background -->
    <div class="stats__bg-shape stats__bg-shape--1"></div>
    <div class="stats__bg-shape stats__bg-shape--2"></div>
    <div class="stats__bg-shape stats__bg-shape--3"></div>

    <div class="stats__container">
      <span class="stats__badge">🌍 Real numbers, real impact</span>
      <h2 class="stats__title">Impact so far</h2>
      <p class="stats__subtitle">Every kilogram saved is a step towards a circular construction industry.</p>

      <div class="stats__grid">
        <div
          v-for="(stat, i) in stats"
          :key="stat.label"
          class="stats__card"
          :class="'stats__card--' + (i + 1)"
        >
          <div class="stats__icon-ring">
            <span class="stats__emoji">{{ stat.emoji }}</span>
          </div>
          <span class="stats__value">{{ stat.value }}</span>
          <span class="stats__label">{{ stat.label }}</span>
          <div class="stats__bar">
            <div class="stats__bar-fill" :style="{ width: stat.bar }"></div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const stats = [
  { emoji: '♻️', value: '12,400 kg', label: 'Materials saved from landfill', bar: '78%' },
  { emoji: '🏗️', value: '6', label: 'Demolition projects tracked', bar: '60%' },
  { emoji: '💰', value: '€240,000', label: 'Total reused value', bar: '90%' },
]
</script>

<style scoped>
.stats {
  position: relative;
  padding: 80px 24px 88px;
  background: linear-gradient(160deg, var(--color-green-dark) 0%, #163d20 40%, var(--color-brown-dark) 100%);
  overflow: hidden;
}

/* floating background shapes */
.stats__bg-shape {
  position: absolute;
  border-radius: 50%;
  opacity: 0.06;
  pointer-events: none;
}
.stats__bg-shape--1 {
  width: 400px; height: 400px;
  background: #fff;
  top: -120px; left: -80px;
}
.stats__bg-shape--2 {
  width: 260px; height: 260px;
  background: var(--color-green);
  bottom: -60px; right: 10%;
}
.stats__bg-shape--3 {
  width: 180px; height: 180px;
  background: #fff;
  top: 40%; right: -40px;
}

.stats__container {
  position: relative;
  max-width: 1100px;
  margin: 0 auto;
  text-align: center;
}

.stats__badge {
  display: inline-block;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.15);
  color: rgba(255, 255, 255, 0.85);
  font-size: 0.82rem;
  font-weight: 600;
  padding: 6px 18px;
  border-radius: 50px;
  letter-spacing: 0.03em;
  margin-bottom: 16px;
  backdrop-filter: blur(4px);
}

.stats__title {
  font-size: 2.4rem;
  font-weight: 800;
  color: #fff;
  margin: 0 0 10px;
  letter-spacing: -0.02em;
}

.stats__subtitle {
  font-size: 1.05rem;
  color: rgba(255, 255, 255, 0.6);
  margin: 0 0 44px;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
  line-height: 1.5;
}

.stats__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.stats__card {
  background: rgba(255, 255, 255, 0.07);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 36px 28px 30px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  backdrop-filter: blur(12px);
  transition: transform 0.3s, box-shadow 0.3s, background 0.3s;
}
.stats__card:hover {
  transform: translateY(-6px);
  background: rgba(255, 255, 255, 0.12);
  box-shadow: 0 16px 48px rgba(0, 0, 0, 0.25);
}

.stats__icon-ring {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  background: linear-gradient(135deg, rgba(255,255,255,0.15), rgba(255,255,255,0.05));
  border: 2px solid rgba(255, 255, 255, 0.12);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 8px;
}

.stats__emoji {
  font-size: 1.7rem;
}

.stats__value {
  font-size: 2.6rem;
  font-weight: 800;
  color: #fff;
  line-height: 1.1;
  letter-spacing: -0.02em;
}

.stats__label {
  font-size: 0.88rem;
  color: rgba(255, 255, 255, 0.55);
  font-weight: 500;
  line-height: 1.4;
  max-width: 200px;
}

.stats__bar {
  width: 100%;
  max-width: 160px;
  height: 5px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  margin-top: 10px;
  overflow: hidden;
}
.stats__bar-fill {
  height: 100%;
  border-radius: 10px;
  background: linear-gradient(90deg, var(--color-green), #6dd994);
  transition: width 1s ease;
}

/* card accent top borders */
.stats__card--1 { border-top: 3px solid rgba(109, 217, 148, 0.5); }
.stats__card--2 { border-top: 3px solid rgba(255, 200, 87, 0.5); }
.stats__card--3 { border-top: 3px solid rgba(130, 200, 255, 0.5); }

@media (max-width: 768px) {
  .stats { padding: 56px 20px 64px; }
  .stats__title { font-size: 1.9rem; }
  .stats__grid { grid-template-columns: 1fr; max-width: 380px; margin: 0 auto; }
  .stats__value { font-size: 2.1rem; }
}
</style>
