<template>
  <section class="hero">
    <div class="hero__container">
      <h1 class="hero__title">Reuse Construction Materials</h1>
      <p class="hero__sub">Before They Become Waste</p>

      <form class="hero__search" @submit.prevent="handleSearch">
        <label for="hero-search" class="sr-only">Search materials</label>
        <div class="hero__search-wrap">
          <input
            id="hero-search"
            v-model="searchText"
            type="text"
            placeholder="Search materials…"
            class="hero__input"
          />
          <button type="submit" class="hero__search-btn" aria-label="Search">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
          </button>
        </div>
      </form>

      <NuxtLink to="/marketplace" class="hero__cta">Browse Marketplace</NuxtLink>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const router = useRouter()
const searchText = ref('')

function handleSearch() {
  const q = searchText.value.trim()
  if (q) {
    router.push({ path: '/marketplace', query: { search: q } })
  } else {
    router.push('/marketplace')
  }
}
</script>

<style scoped>
.hero {
  padding: 64px 24px 56px;
  text-align: center;
}
.hero__container {
  max-width: 680px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.hero__title {
  font-size: 2.8rem;
  font-weight: 800;
  color: var(--color-green-dark);
  margin: 0;
  line-height: 1.15;
}
.hero__sub {
  font-size: 1.25rem;
  color: var(--color-brown);
  margin: 14px 0 0;
  font-weight: 400;
}
.hero__search {
  margin-top: 28px;
  width: 100%;
  max-width: 480px;
}
.hero__search-wrap {
  display: flex;
  border: 2px solid var(--color-green);
  border-radius: 12px;
  overflow: hidden;
  background: #fff;
}
.hero__input {
  flex: 1;
  border: none;
  outline: none;
  padding: 14px 18px;
  font-size: 1rem;
  background: transparent;
  color: #333;
}
.hero__input::placeholder {
  color: #999;
}
.hero__search-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 16px;
  background: var(--color-green);
  border: none;
  color: #fff;
  cursor: pointer;
  transition: background 0.2s;
}
.hero__search-btn:hover {
  background: var(--color-green-dark);
}
.hero__cta {
  display: inline-block;
  text-decoration: none;
  margin-top: 20px;
  padding: 14px 36px;
  font-size: 1.05rem;
  font-weight: 700;
  color: #fff;
  background: var(--color-green);
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: background 0.2s, transform 0.15s;
}
.hero__cta:hover {
  background: var(--color-green-dark);
  transform: translateY(-1px);
}

/* visually hidden label for a11y */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

@media (max-width: 600px) {
  .hero { padding: 40px 20px 36px; }
  .hero__title { font-size: 2rem; }
  .hero__sub { font-size: 1.05rem; }
  .hero__cta { width: 100%; }
  .hero__search { max-width: 100%; }
}
</style>
