<script setup>
import { computed } from 'vue'
import { Flame } from 'lucide-vue-next'
import ScrollReveal from '@/components/ui/ScrollReveal.vue'
import SectionHeading from '@/components/ui/SectionHeading.vue'
import { weeklySchedule } from '@/data/schedule.js'

const todayIndex = computed(() => {
  const jsDay = new Date().getDay()
  // JS: 0=Sunday, 1=Monday ... 6=Saturday
  // Schedule: 0=Luni(Monday), 1=Marti ... 5=Sambata(Saturday)
  // Sunday has no schedule entry
  if (jsDay === 0) return -1
  return jsDay - 1
})
</script>

<template>
  <section id="program" class="bg-surface-light py-20 lg:py-28">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-12">
      <ScrollReveal>
        <SectionHeading
          light
          label="PROGRAM PAINE"
          title="Programul Saptamanal al Painii"
          subtitle="Aflati ce paine proaspata va asteapta in fiecare zi"
        />
      </ScrollReveal>

      <ScrollReveal :delay="200">
        <div class="flex gap-4 overflow-x-auto snap-x snap-mandatory pb-4 px-4 -mx-4">
          <div
            v-for="(day, index) in weeklySchedule"
            :key="day.day"
            class="snap-start min-w-[260px] w-72 flex-shrink-0 rounded-2xl bg-white shadow-md p-5 relative"
            :class="index === todayIndex
              ? 'border-2 border-brand shadow-lg'
              : 'border border-border-light'"
          >
            <!-- Today badge -->
            <span
              v-if="index === todayIndex"
              class="absolute top-3 right-3 bg-brand text-white text-xs font-bold px-2.5 py-0.5 rounded-full"
            >
              Azi
            </span>

            <!-- Day name -->
            <h3 class="font-heading text-lg font-bold text-text-dark mb-3">
              {{ day.day }}
            </h3>

            <!-- Regular breads -->
            <ul class="space-y-1.5 mb-3">
              <li
                v-for="bread in day.regular"
                :key="bread"
                class="text-text-dark-secondary text-sm leading-snug"
              >
                {{ bread }}
              </li>
            </ul>

            <!-- Specials -->
            <template v-if="day.specials && day.specials.length > 0">
              <div class="border-t border-border-light my-3"></div>
              <ul class="space-y-1.5">
                <li
                  v-for="special in day.specials"
                  :key="special"
                  class="flex items-start gap-1.5 text-sm leading-snug"
                >
                  <Flame :size="14" class="text-brand mt-0.5 flex-shrink-0" />
                  <span class="text-brand-dark font-medium">{{ special }}</span>
                </li>
              </ul>
            </template>
          </div>
        </div>
      </ScrollReveal>
    </div>
  </section>
</template>
