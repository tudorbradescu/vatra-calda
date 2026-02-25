<script setup>
import { Star } from 'lucide-vue-next'
import ScrollReveal from '@/components/ui/ScrollReveal.vue'
import SectionHeading from '@/components/ui/SectionHeading.vue'
import { testimonials, googleRating } from '@/data/testimonials.js'
</script>

<template>
  <section class="bg-surface-primary py-20 lg:py-28">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-12">
      <ScrollReveal>
        <SectionHeading
          label="RECENZII"
          title="Ce Spun Clientii Nostri"
        />
      </ScrollReveal>

      <!-- Google rating badge -->
      <ScrollReveal :delay="100">
        <div class="flex flex-col items-center mb-12">
          <div class="flex items-center gap-3 mb-2">
            <span class="text-5xl font-heading font-bold text-text-primary">
              {{ googleRating.score }}
            </span>
            <div class="flex items-center gap-0.5">
              <Star
                v-for="i in 5"
                :key="i"
                :size="22"
                class="text-star"
                :fill="i <= Math.floor(googleRating.score) ? 'currentColor' : (i === Math.ceil(googleRating.score) ? 'currentColor' : 'none')"
                :style="i === Math.ceil(googleRating.score) && googleRating.score % 1 !== 0
                  ? { clipPath: `inset(0 ${(1 - (googleRating.score % 1)) * 100}% 0 0)` }
                  : {}"
              />
            </div>
          </div>
          <p class="text-text-secondary text-sm">
            {{ googleRating.total }} recenzii pe Google
          </p>
        </div>
      </ScrollReveal>

      <!-- Testimonial cards -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-12">
        <ScrollReveal
          v-for="(testimonial, index) in testimonials"
          :key="testimonial.name"
          :delay="index * 150"
        >
          <div class="bg-surface-card rounded-2xl p-6 border border-border-subtle h-full flex flex-col">
            <!-- Star rating -->
            <div class="flex items-center gap-0.5 mb-4">
              <Star
                v-for="i in 5"
                :key="i"
                :size="16"
                class="text-star"
                :fill="i <= testimonial.rating ? 'currentColor' : 'none'"
              />
            </div>

            <!-- Quote -->
            <p class="text-text-secondary italic leading-relaxed flex-1 mb-5">
              &ldquo;{{ testimonial.text }}&rdquo;
            </p>

            <!-- Reviewer info -->
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 rounded-full bg-brand/20 flex items-center justify-center">
                <span class="text-brand font-semibold text-sm">
                  {{ testimonial.name.charAt(0) }}
                </span>
              </div>
              <div>
                <div class="flex items-center gap-2">
                  <span class="text-text-primary font-semibold text-sm">
                    {{ testimonial.name }}
                  </span>
                  <span v-if="testimonial.badge" class="text-brand text-xs font-medium">
                    {{ testimonial.badge }}
                  </span>
                </div>
                <span class="text-text-muted text-xs">
                  {{ testimonial.time }}
                </span>
              </div>
            </div>
          </div>
        </ScrollReveal>
      </div>

      <!-- CTA buttons -->
      <ScrollReveal :delay="300">
        <div class="flex flex-wrap justify-center gap-4">
          <a
            href="https://www.google.com/maps/place/VATRA+CALDA+(Aradul+Nou)/@46.1525913,21.3222423,17z"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center gap-2 border border-text-secondary text-text-primary hover:border-brand hover:text-brand px-6 py-3 rounded-xl font-semibold transition-colors duration-200"
          >
            Scrie o recenzie pe Google
          </a>
          <a
            href="https://www.facebook.com/vatracaldaarad"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center gap-2 border border-text-secondary text-text-primary hover:border-brand hover:text-brand px-6 py-3 rounded-xl font-semibold transition-colors duration-200"
          >
            Urmareste-ne pe Facebook
          </a>
        </div>
      </ScrollReveal>
    </div>
  </section>
</template>
