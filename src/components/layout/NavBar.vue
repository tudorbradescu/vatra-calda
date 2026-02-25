<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Phone, Menu, X } from 'lucide-vue-next'

const scrolled = ref(false)
const menuOpen = ref(false)

const navLinks = [
  { label: 'Povestea Noastra', href: '#despre' },
  { label: 'Meniu', href: '#meniu' },
  { label: 'Program Paine', href: '#program' },
  { label: 'Galerie', href: '#galerie' },
  { label: 'Contact', href: '#contact' }
]

const handleScroll = () => {
  scrolled.value = window.scrollY > 80
}

const closeMenu = () => {
  menuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav
    class="fixed top-0 left-0 right-0 z-50 transition-all duration-300"
    :class="scrolled || menuOpen ? 'bg-surface-primary/95 backdrop-blur-md shadow-lg shadow-black/20' : 'bg-transparent'"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-20">
        <!-- Logo -->
        <a href="#" class="shrink-0 flex items-center gap-2">
          <span class="font-heading text-2xl font-bold text-text-primary">Vatra</span>
          <span class="font-heading text-2xl font-bold text-brand">Calda</span>
        </a>

        <!-- Desktop nav links -->
        <div class="hidden lg:flex items-center gap-8">
          <a
            v-for="link in navLinks"
            :key="link.href"
            :href="link.href"
            class="text-sm font-medium text-text-secondary hover:text-text-primary transition-colors duration-200"
          >
            {{ link.label }}
          </a>
        </div>

        <!-- Desktop phone CTA -->
        <a
          href="tel:0754696028"
          class="hidden lg:flex items-center gap-2 bg-brand hover:bg-brand-light text-white px-5 py-2.5 rounded-xl text-sm font-semibold transition-colors duration-200"
        >
          <Phone :size="16" />
          0754 696 028
        </a>

        <!-- Mobile buttons -->
        <div class="flex lg:hidden items-center gap-3">
          <a href="tel:0754696028" class="bg-brand p-2.5 rounded-xl text-white">
            <Phone :size="18" />
          </a>
          <button @click="menuOpen = !menuOpen" class="text-white p-2">
            <X v-if="menuOpen" :size="24" />
            <Menu v-else :size="24" />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile menu -->
    <Transition
      enter-active-class="transition-all duration-300 ease-out"
      enter-from-class="opacity-0 -translate-y-4"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition-all duration-200 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-4"
    >
      <div v-if="menuOpen" class="lg:hidden bg-surface-primary/95 backdrop-blur-md border-t border-border-subtle">
        <div class="px-4 py-6 space-y-1">
          <a
            v-for="link in navLinks"
            :key="link.href"
            :href="link.href"
            @click="closeMenu"
            class="block px-4 py-3 text-text-secondary hover:text-text-primary hover:bg-surface-card rounded-xl transition-colors duration-200 font-medium"
          >
            {{ link.label }}
          </a>
        </div>
      </div>
    </Transition>
  </nav>
</template>
