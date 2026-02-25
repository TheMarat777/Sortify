<template>
  <section id="how-it-works" class="hiw">
    <div class="hiw__container">
      <h2 class="hiw__title">How it works</h2>

      <div class="hiw__grid">
        <div v-for="step in steps" :key="step.num" class="hiw__card">
          <div class="hiw__icon" :aria-label="'Step ' + step.num">{{ step.num }}</div>
          <h3 class="hiw__card-title">{{ step.title }}</h3>
          <p class="hiw__card-desc">{{ step.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const steps = [
  { num: '1', title: 'Register materials', desc: 'List leftover construction materials before demolition begins.' },
  { num: '2', title: 'Buyers find them', desc: 'Contractors and builders browse available resources nearby.' },
  { num: '3', title: 'Sell before demolition ends', desc: 'Materials get reused instead of going to landfill.' },
]
</script>

<style scoped>
.hiw {
  padding: 64px 24px;
  background: #e8f5e9;
}
.hiw__container {
  max-width: 1100px;
  margin: 0 auto;
}
.hiw__title {
  text-align: center;
  font-size: 2rem;
  font-weight: 800;
  color: var(--color-green-dark);
  margin: 0 0 32px;
}
.hiw__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.hiw__card {
  background: #fff;
  border: 1px solid rgba(47, 122, 62, 0.12);
  border-radius: 14px;
  padding: 28px 24px;
  text-align: center;
  transition: box-shadow 0.2s;
}
.hiw__card:hover {
  box-shadow: 0 4px 20px rgba(47, 122, 62, 0.1);
}
.hiw__icon {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: var(--color-green);
  color: #fff;
  font-size: 1.3rem;
  font-weight: 800;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 16px;
}
.hiw__card-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--color-green-dark);
  margin: 0 0 8px;
}
.hiw__card-desc {
  font-size: 0.92rem;
  color: #666;
  margin: 0;
  line-height: 1.5;
}

@media (max-width: 768px) {
  .hiw { padding: 40px 20px; }
  .hiw__grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 500px) {
  .hiw__grid { grid-template-columns: 1fr; }
}
</style>
