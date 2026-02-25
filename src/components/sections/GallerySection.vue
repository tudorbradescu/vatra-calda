<script setup>
import { ref, computed } from 'vue'
import { ZoomIn } from 'lucide-vue-next'
import ScrollReveal from '@/components/ui/ScrollReveal.vue'
import SectionHeading from '@/components/ui/SectionHeading.vue'
import LightboxModal from '@/components/ui/LightboxModal.vue'
import { galleryImages, featuredGalleryIndexes } from '@/data/gallery.js'

const lightboxOpen = ref(false)
const lightboxStart = ref(0)

const featuredImages = computed(() =>
  featuredGalleryIndexes.map((i) => galleryImages[i])
)

const tallIndexes = [0, 3, 8]

function openLightbox(index) {
  lightboxStart.value = index
  lightboxOpen.value = true
}
</script>

<template>
  <section id="galerie" class="bg-surface-secondary py-20 lg:py-28">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-12">
      <ScrollReveal>
        <SectionHeading
          label="GALERIE"
          title="Din Cuptorul Nostru"
        />
      </ScrollReveal>

      <ScrollReveal :delay="150">
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-3 auto-rows-[200px]">
          <div
            v-for="(image, index) in featuredImages"
            :key="image.src"
            class="overflow-hidden rounded-xl cursor-pointer group relative"
            :class="tallIndexes.includes(index) ? 'row-span-2' : ''"
            @click="openLightbox(index)"
          >
            <img
              :src="image.src"
              :alt="image.alt"
              class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-108"
              loading="lazy"
            />
            <div class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <ZoomIn :size="28" class="text-white" />
            </div>
          </div>
        </div>
      </ScrollReveal>

      <!-- View all button -->
      <ScrollReveal :delay="300">
        <div class="mt-10 text-center">
          <a
            href="https://www.facebook.com/vatracaldaarad/photos"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center gap-2 border border-text-secondary text-text-primary hover:border-brand hover:text-brand px-6 py-3 rounded-xl font-semibold transition-colors duration-200"
          >
            Vezi toate fotografiile
          </a>
        </div>
      </ScrollReveal>
    </div>

    <!-- Lightbox -->
    <LightboxModal
      v-if="lightboxOpen"
      :images="featuredImages"
      :start-index="lightboxStart"
      @close="lightboxOpen = false"
    />
  </section>
</template>
