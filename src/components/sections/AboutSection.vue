<script setup>
import ScrollReveal from '@/components/ui/ScrollReveal.vue'
import SectionHeading from '@/components/ui/SectionHeading.vue'

const stats = [
  { number: '50+', label: 'varietati' },
  { number: '6', label: 'zile pe saptamana' },
  { number: '3', label: 'locatii' },
  { number: '100%', label: 'natural' },
]
</script>

<template>
  <section id="despre" class="bg-surface-light py-20 lg:py-28">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-12">
      <ScrollReveal>
        <SectionHeading
          light
          label="DESPRE NOI"
          title="Pasiunea pentru painea adevarata"
        />
      </ScrollReveal>

      <!-- Two columns -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-16 items-center">
        <!-- Left: Text -->
        <ScrollReveal direction="left">
          <div class="space-y-6">
            <p class="text-text-dark-secondary text-base sm:text-lg leading-relaxed">
              La Vatra Calda, fiecare paine este rezultatul unui proces lent si atent, in care timpul si rabdarea sunt ingredientele principale. Maiaua noastra, hranita zilnic cu grija, este inima brutariei - o cultura vie care da fiecarei paini un gust unic si o textura de neuitat.
            </p>
            <p class="text-text-dark-secondary text-base sm:text-lg leading-relaxed">
              In fiecare dimineata, brutarii nostri incep lucrul inainte de rasaritul soarelui, framantand si coacand cu aceeasi dedicare pe care am avut-o din prima zi. Folosim fainuri selectionate cu grija, ingrediente naturale si tehnici artizanale transmise din generatie in generatie.
            </p>
            <p class="text-text-dark-secondary text-base sm:text-lg leading-relaxed">
              Credem ca painea adevarata merita timp. De aceea, aluaturile noastre fermenteaza lent, intre 12 si 24 de ore, pentru a dezvolta arome complexe si o digestibilitate superioara. Fara aditivi, fara grabiri - doar faina, apa, sare si maia.
            </p>

            <!-- Quote block -->
            <blockquote class="border-l-4 border-brand pl-6 py-2 my-8">
              <p class="text-text-dark font-heading italic text-lg sm:text-xl leading-relaxed">
                &ldquo;Fiecare paine spune o poveste - de la maiaua noastra cu ani de experienta, la cuptor, si apoi la masa voastra.&rdquo;
              </p>
            </blockquote>
          </div>
        </ScrollReveal>

        <!-- Right: Image -->
        <ScrollReveal direction="right">
          <div class="relative">
            <img
              src="/photos/602874397_18086053463016595_3562191318699356913_n.jpg"
              alt="Paine artizanala Vatra Calda"
              class="w-full rounded-2xl shadow-xl object-cover"
              loading="lazy"
            />
          </div>
        </ScrollReveal>
      </div>

      <!-- Stats row -->
      <ScrollReveal :delay="200">
        <div class="mt-16 grid grid-cols-2 md:grid-cols-4 gap-8">
          <div
            v-for="stat in stats"
            :key="stat.label"
            class="text-center"
          >
            <div class="text-brand font-heading font-bold text-4xl sm:text-5xl">
              {{ stat.number }}
            </div>
            <div class="mt-2 text-text-dark-secondary text-sm uppercase tracking-wider">
              {{ stat.label }}
            </div>
          </div>
        </div>
      </ScrollReveal>
    </div>
  </section>
</template>
