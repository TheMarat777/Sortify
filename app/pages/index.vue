<template>
  <main class="main-content">
    <HeroSection />
    <HowItWorksSection />
    <StatsSection />
  </main>
</template>

<script setup>
import HeroSection from '../../components/HeroSection.vue'
import HowItWorksSection from '../../components/HowItWorksSection.vue'
import StatsSection from '../../components/StatsSection.vue'
</script>

<style scoped>
.main-content {
  flex: 1;
}
</style>
