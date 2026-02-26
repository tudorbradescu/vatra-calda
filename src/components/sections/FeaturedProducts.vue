<script setup>
import ScrollReveal from '@/components/ui/ScrollReveal.vue'
import SectionHeading from '@/components/ui/SectionHeading.vue'

const base = import.meta.env.BASE_URL

const products = [
  {
    name: 'Paine Vatra Calda',
    description: 'Painea noastra emblematica cu maia',
    price: 'de la 13.20 lei',
    image: `${base}photos/597218030_1410217691113079_6378883580775323616_n.jpg`,
  },
  {
    name: 'Croissant cu Fistic',
    description: 'Plin de crema, interior si exterior',
    price: '20.50 lei',
    image: `${base}photos/631534859_1459440092857505_5297671020940052993_n.jpg`,
  },
  {
    name: 'Pasteis de Nata',
    description: 'Reteta autentica portugheza',
    price: '10 lei',
    image: `${base}photos/625681126_1453424923459022_4433757549154012074_n.jpg`,
  },
  {
    name: 'Focaccia Artizanala',
    description: 'Cu topping-uri diverse',
    price: 'de la 14 lei',
    image: `${base}photos/625932023_1450649813736533_519456075658898453_n.jpg`,
  },
]
</script>

<template>
  <section class="bg-surface-primary py-20 lg:py-28">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-12">
      <ScrollReveal>
        <SectionHeading
          label="PRODUSE VEDETA"
          title="Gusturi care inspira"
        />
      </ScrollReveal>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <ScrollReveal
          v-for="(product, index) in products"
          :key="product.name"
          :delay="index * 150"
        >
          <div class="group relative aspect-[3/4] overflow-hidden rounded-2xl cursor-pointer">
            <!-- Image -->
            <img
              :src="product.image"
              :alt="product.name"
              class="absolute inset-0 w-full h-full object-cover transition-transform duration-500 group-hover:scale-108"
              loading="lazy"
            />
            <!-- Gradient overlay -->
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/10 to-transparent"></div>
            <!-- Content at bottom -->
            <div class="absolute bottom-0 left-0 right-0 p-5">
              <h3 class="font-heading text-xl font-bold text-text-primary mb-1">
                {{ product.name }}
              </h3>
              <p class="text-text-secondary text-sm mb-3">
                {{ product.description }}
              </p>
              <span class="inline-block bg-brand/90 text-white text-sm font-semibold px-3 py-1 rounded-lg">
                {{ product.price }}
              </span>
            </div>
          </div>
        </ScrollReveal>
      </div>
    </div>
  </section>
</template>
