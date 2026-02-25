<script setup>
import { ref, computed } from 'vue'
import ScrollReveal from '@/components/ui/ScrollReveal.vue'
import SectionHeading from '@/components/ui/SectionHeading.vue'
import { menuCategories } from '@/data/menu.js'

const activeTab = ref('paine')

const activeCategory = computed(() =>
  menuCategories.find((c) => c.id === activeTab.value)
)

function formatPrice(price) {
  if (Number.isInteger(price)) return `${price} lei`
  return `${price.toFixed(2)} lei`
}
</script>

<template>
  <section id="meniu" class="bg-surface-primary py-20 lg:py-28">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-12">
      <ScrollReveal>
        <SectionHeading
          label="MENIU"
          title="Meniul Nostru Complet"
        />
      </ScrollReveal>

      <!-- Tab bar -->
      <ScrollReveal :delay="100">
        <div class="flex gap-2 overflow-x-auto pb-2 mb-10 scrollbar-none">
          <button
            v-for="category in menuCategories"
            :key="category.id"
            class="px-5 py-2.5 rounded-full text-sm font-semibold transition-all whitespace-nowrap flex-shrink-0"
            :class="activeTab === category.id
              ? 'bg-brand text-white'
              : 'text-text-secondary hover:text-text-primary'"
            @click="activeTab = category.id"
          >
            {{ category.label }}
          </button>
        </div>
      </ScrollReveal>

      <!-- Product grid with transition -->
      <Transition name="menu-fade" mode="out-in">
        <div
          v-if="activeCategory"
          :key="activeCategory.id"
          class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4"
        >
          <div
            v-for="item in activeCategory.items"
            :key="item.name"
            class="bg-surface-card rounded-xl p-5 hover:bg-surface-card-hover transition-all duration-200 hover:-translate-y-0.5"
          >
            <h3 class="font-heading font-semibold text-text-primary mb-2">
              {{ item.name }}
            </h3>
            <div
              v-for="(variant, vi) in item.variants"
              :key="vi"
              class="flex items-center justify-between"
              :class="item.variants.length > 1 ? 'mt-1' : ''"
            >
              <span v-if="variant.w" class="text-text-muted text-sm">
                {{ variant.w }}
              </span>
              <span v-else class="text-text-muted text-sm">&nbsp;</span>
              <span class="text-brand font-bold">
                {{ formatPrice(variant.p) }}
              </span>
            </div>
          </div>
        </div>
      </Transition>
    </div>
  </section>
</template>

<style scoped>
.menu-fade-enter-active,
.menu-fade-leave-active {
  transition: opacity 0.25s ease;
}
.menu-fade-enter-from,
.menu-fade-leave-to {
  opacity: 0;
}

.scrollbar-none::-webkit-scrollbar {
  display: none;
}
.scrollbar-none {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>
