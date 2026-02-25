<script setup>
import { ref, onMounted } from 'vue'
import { Phone } from 'lucide-vue-next'

const show = ref(false)

onMounted(() => {
  setTimeout(() => { show.value = true }, 2000)
})
</script>

<template>
  <Transition name="phone-float">
    <a
      v-if="show"
      href="tel:0754696028"
      class="fixed bottom-6 right-6 z-50 flex items-center justify-center w-14 h-14 bg-brand hover:bg-brand-light text-white rounded-full shadow-lg transition-colors duration-200 group"
      style="animation: phone-pulse 2s infinite"
      aria-label="Suna pentru comanda"
    >
      <Phone :size="24" />
      <span class="absolute right-full mr-3 px-3 py-1.5 bg-surface-primary/95 text-text-primary text-sm rounded-lg whitespace-nowrap opacity-0 group-hover:opacity-100 transition-opacity duration-200 pointer-events-none">
        Suna pentru comanda
      </span>
    </a>
  </Transition>
</template>
