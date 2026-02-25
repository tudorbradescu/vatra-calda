<script setup>
import { Phone, Star, MapPin, Clock } from 'lucide-vue-next'

const props = defineProps({
  animate: { type: Boolean, default: false }
})
</script>

<template>
  <section class="relative min-h-screen flex items-center overflow-hidden">
    <!-- Background image with slow zoom -->
    <div
      class="absolute inset-0 bg-cover bg-center"
      style="
        background-image: url('https://images.unsplash.com/photo-1509440159596-0249088772ff?w=1920&q=80&auto=format&fit=crop');
        animation: slow-zoom 25s ease-in-out infinite alternate;
        transform-origin: center center;
      "
    ></div>

    <!-- Dark gradient overlay -->
    <div class="absolute inset-0 bg-gradient-to-r from-black/80 via-surface-primary/70 to-transparent"></div>

    <!-- Content -->
    <div class="relative z-10 w-full max-w-7xl mx-auto px-6 sm:px-8 lg:px-12 py-24">
      <!-- Badge pill -->
      <div
        class="transition-all duration-700"
        :class="animate ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-[30px]'"
        :style="{ transitionDelay: animate ? '100ms' : '0ms', transitionTimingFunction: 'cubic-bezier(0.16, 1, 0.3, 1)' }"
      >
        <span class="inline-flex items-center gap-2 px-4 py-2 rounded-full border border-text-secondary/30 bg-white/5 backdrop-blur-sm text-text-secondary text-sm tracking-wide">
          <span class="w-2 h-2 rounded-full bg-brand"></span>
          Brutarie Artizanala din Arad
        </span>
      </div>

      <!-- Large heading -->
      <h1
        class="mt-6 font-heading text-5xl sm:text-6xl lg:text-8xl font-bold leading-tight transition-all duration-700"
        :class="animate ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-[30px]'"
        :style="{ transitionDelay: animate ? '300ms' : '0ms', transitionTimingFunction: 'cubic-bezier(0.16, 1, 0.3, 1)' }"
      >
        <span class="text-text-primary block">Vatra</span>
        <span class="text-brand block">Calda</span>
      </h1>

      <!-- Tagline -->
      <p
        class="mt-4 text-xl sm:text-2xl text-text-secondary font-heading italic transition-all duration-700"
        :class="animate ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-[30px]'"
        :style="{ transitionDelay: animate ? '500ms' : '0ms', transitionTimingFunction: 'cubic-bezier(0.16, 1, 0.3, 1)' }"
      >
        arta painii cu maia
      </p>

      <!-- Description -->
      <p
        class="mt-5 text-text-secondary text-base sm:text-lg max-w-lg leading-relaxed transition-all duration-700"
        :class="animate ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-[30px]'"
        :style="{ transitionDelay: animate ? '650ms' : '0ms', transitionTimingFunction: 'cubic-bezier(0.16, 1, 0.3, 1)' }"
      >
        Paine cu maia, croissante si patiserie artizanala, coapte cu pasiune in fiecare dimineata.
      </p>

      <!-- CTA Buttons -->
      <div
        class="mt-8 flex flex-wrap items-center gap-4 transition-all duration-700"
        :class="animate ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-[30px]'"
        :style="{ transitionDelay: animate ? '800ms' : '0ms', transitionTimingFunction: 'cubic-bezier(0.16, 1, 0.3, 1)' }"
      >
        <a
          href="tel:0754696028"
          class="inline-flex items-center gap-2 bg-brand hover:bg-brand-light text-white px-6 py-3 rounded-xl font-semibold transition-colors duration-200"
          :style="animate ? 'animation: pulse-glow 3s ease-in-out infinite' : ''"
        >
          <Phone :size="18" />
          Suna pentru Comanda
        </a>
        <a
          href="#meniu"
          class="inline-flex items-center gap-2 border border-text-secondary text-text-primary hover:border-brand px-6 py-3 rounded-xl font-semibold transition-colors duration-200"
        >
          Vezi Meniul
        </a>
      </div>

      <!-- Trust badges -->
      <div
        class="mt-10 flex flex-wrap items-center gap-6 text-text-secondary text-sm transition-all duration-700"
        :class="animate ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-[30px]'"
        :style="{ transitionDelay: animate ? '1000ms' : '0ms', transitionTimingFunction: 'cubic-bezier(0.16, 1, 0.3, 1)' }"
      >
        <span class="inline-flex items-center gap-1.5">
          <Star :size="16" class="text-star" />
          4.6 stele Google
        </span>
        <span class="w-px h-4 bg-text-secondary/30 hidden sm:block"></span>
        <span class="inline-flex items-center gap-1.5">
          <MapPin :size="16" class="text-brand" />
          3 locatii in Arad
        </span>
        <span class="w-px h-4 bg-text-secondary/30 hidden sm:block"></span>
        <span class="inline-flex items-center gap-1.5">
          <Clock :size="16" class="text-brand" />
          Luni - Sambata
        </span>
      </div>
    </div>
  </section>
</template>
