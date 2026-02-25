<script setup>
import { ref } from 'vue'
import LoaderScreen from '@/components/ui/LoaderScreen.vue'
import NavBar from '@/components/layout/NavBar.vue'
import FooterSection from '@/components/layout/FooterSection.vue'
import HeroSection from '@/components/sections/HeroSection.vue'
import AboutSection from '@/components/sections/AboutSection.vue'
import FeaturedProducts from '@/components/sections/FeaturedProducts.vue'
import BreadSchedule from '@/components/sections/BreadSchedule.vue'
import MenuSection from '@/components/sections/MenuSection.vue'
import GallerySection from '@/components/sections/GallerySection.vue'
import TestimonialsSection from '@/components/sections/TestimonialsSection.vue'
import LocationsSection from '@/components/sections/LocationsSection.vue'
import PhoneFloat from '@/components/ui/PhoneFloat.vue'

const loaderDone = ref(false)
</script>

<template>
  <LoaderScreen @done="loaderDone = true" />
  <div class="min-h-screen bg-surface-primary text-text-primary">
    <NavBar />
    <main>
      <HeroSection :animate="loaderDone" />
      <AboutSection />
      <FeaturedProducts />
      <BreadSchedule />
      <MenuSection />
      <GallerySection />
      <TestimonialsSection />
      <LocationsSection />
    </main>
    <FooterSection />
    <PhoneFloat />
  </div>
</template>
