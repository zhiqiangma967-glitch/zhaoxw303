<script setup>
import SiteHeader from './components/SiteHeader.vue'
import HeroSection from './components/HeroSection.vue'
import MenuSection from './components/MenuSection.vue'
import StorySection from './components/StorySection.vue'
import ReservationSection from './components/ReservationSection.vue'
import SiteFooter from './components/SiteFooter.vue'
</script>

<template>
  <div class="wrap">
    <SiteHeader />
    <main>
      <HeroSection />
      <MenuSection />
      <StorySection />
      <ReservationSection />
    </main>
    <SiteFooter />
  </div>
</template>
