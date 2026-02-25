<script setup>
import { Phone, Star, ExternalLink } from 'lucide-vue-next'
import ScrollReveal from '@/components/ui/ScrollReveal.vue'
import SectionHeading from '@/components/ui/SectionHeading.vue'
import { locations } from '@/data/locations.js'
</script>

<template>
  <section id="contact" class="bg-surface-light py-20 lg:py-28">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-12">
      <ScrollReveal>
        <SectionHeading
          light
          label="LOCATII"
          title="Ne Gasesti in 3 Locatii din Arad"
        />
      </ScrollReveal>

      <!-- Location cards -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-16">
        <ScrollReveal
          v-for="(location, index) in locations"
          :key="location.name"
          :delay="index * 150"
        >
          <div class="bg-white rounded-2xl overflow-hidden shadow-md border border-border-light h-full flex flex-col">
            <!-- Map embed -->
            <div class="h-48 w-full">
              <iframe
                :src="location.embedUrl"
                class="w-full h-full border-0"
                allowfullscreen=""
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
                :title="`Harta ${location.name}`"
              ></iframe>
            </div>

            <!-- Content -->
            <div class="p-5 flex flex-col flex-1">
              <h3 class="font-heading font-bold text-text-dark text-lg mb-1">
                {{ location.name }}
              </h3>
              <p class="text-text-dark-secondary text-sm mb-3">
                {{ location.address }}
              </p>

              <!-- Rating -->
              <div class="flex items-center gap-1.5 mb-3">
                <span class="text-text-dark font-semibold text-sm">{{ location.rating }}</span>
                <div class="flex items-center gap-0.5">
                  <Star
                    v-for="i in 5"
                    :key="i"
                    :size="14"
                    class="text-star"
                    :fill="i <= Math.floor(location.rating) ? 'currentColor' : (i === Math.ceil(location.rating) && location.rating % 1 !== 0 ? 'currentColor' : 'none')"
                  />
                </div>
                <span class="text-text-dark-secondary text-xs">({{ location.reviews }})</span>
              </div>

              <!-- Service badges -->
              <div class="flex flex-wrap gap-2 mb-3">
                <span
                  v-for="service in location.services"
                  :key="service"
                  class="inline-flex items-center px-2.5 py-1 bg-surface-light rounded-lg text-text-dark-secondary text-xs font-medium"
                >
                  {{ service }}
                </span>
              </div>

              <!-- Hours -->
              <p class="text-text-dark-secondary text-sm mb-4">
                {{ location.hours }}
              </p>

              <!-- Directions link -->
              <a
                :href="location.mapUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="mt-auto inline-flex items-center gap-1.5 text-brand-dark hover:text-brand font-semibold text-sm transition-colors duration-200"
              >
                <ExternalLink :size="14" />
                Indicatii
              </a>
            </div>
          </div>
        </ScrollReveal>
      </div>

      <!-- Contact info centered -->
      <ScrollReveal :delay="300">
        <div class="text-center space-y-4">
          <!-- Phone -->
          <a
            href="tel:0754696028"
            class="inline-flex items-center gap-3 text-brand text-3xl font-heading font-bold hover:text-brand-dark transition-colors duration-200"
          >
            <Phone :size="28" />
            0754 696 028
          </a>

          <!-- Schedule -->
          <p class="text-text-dark-secondary text-base">
            Luni - Vineri: 09:00 - 17:30
            <span class="mx-2 text-border-light">|</span>
            Sambata: 09:00 - 13:00
            <span class="mx-2 text-border-light">|</span>
            Duminica: Inchis
          </p>

          <!-- Facebook link -->
          <a
            href="https://www.facebook.com/vatracaldaarad"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center gap-2 text-brand-dark hover:text-brand font-semibold transition-colors duration-200"
          >
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="currentColor">
              <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
            </svg>
            Urmareste-ne pe Facebook
          </a>
        </div>
      </ScrollReveal>
    </div>
  </section>
</template>
