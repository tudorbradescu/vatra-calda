<script setup>
import { ref, onMounted } from 'vue'

const emit = defineEmits(['done'])
const show = ref(true)
const lettersVisible = ref(false)
const lineVisible = ref(false)
const subVisible = ref(false)
const slideUp = ref(false)

onMounted(() => {
  document.body.style.overflow = 'hidden'

  // Stagger letters in
  setTimeout(() => { lettersVisible.value = true }, 200)
  // Line grows
  setTimeout(() => { lineVisible.value = true }, 900)
  // Sub text fades in
  setTimeout(() => { subVisible.value = true }, 1200)
  // Hold, then slide up
  setTimeout(() => { slideUp.value = true }, 2200)
  // Remove loader completely
  setTimeout(() => {
    show.value = false
    document.body.style.overflow = ''
    emit('done')
  }, 3100)
})
</script>

<template>
  <div
    v-if="show"
    class="fixed inset-0 z-[10000] flex flex-col items-center justify-center bg-surface-primary transition-transform duration-[900ms]"
    :class="slideUp ? '-translate-y-full' : 'translate-y-0'"
    style="transition-timing-function: cubic-bezier(0.76, 0, 0.24, 1)"
  >
    <!-- Logo letters -->
    <div class="flex items-center gap-0 font-heading text-[clamp(2rem,5vw,4rem)] font-bold tracking-wider">
      <!-- "Vatra" -->
      <div class="flex">
        <span
          v-for="(letter, i) in 'Vatra'.split('')"
          :key="'v' + i"
          class="inline-block text-text-primary transition-all duration-[400ms]"
          :class="lettersVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-[60px]'"
          :style="{ transitionDelay: `${i * 60}ms`, transitionTimingFunction: 'cubic-bezier(0.16, 1, 0.3, 1)' }"
        >{{ letter }}</span>
      </div>
      <!-- space -->
      <div class="w-[0.4em]"></div>
      <!-- "Calda" -->
      <div class="flex">
        <span
          v-for="(letter, i) in 'Calda'.split('')"
          :key="'c' + i"
          class="inline-block text-brand transition-all duration-[400ms]"
          :class="lettersVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-[60px]'"
          :style="{ transitionDelay: `${(i + 5) * 60 + 50}ms`, transitionTimingFunction: 'cubic-bezier(0.16, 1, 0.3, 1)' }"
        >{{ letter }}</span>
      </div>
    </div>

    <!-- Gradient line -->
    <div
      class="h-[2px] rounded-full mt-5 transition-all duration-[600ms] ease-out"
      :class="lineVisible ? 'w-[200px]' : 'w-0'"
      style="background: linear-gradient(90deg, #c8956c, #d4a04a)"
    ></div>

    <!-- Subtitle -->
    <p
      class="mt-4 text-sm tracking-[0.3em] uppercase text-text-muted transition-opacity duration-[400ms]"
      :class="subVisible ? 'opacity-100' : 'opacity-0'"
    >
      arta painii cu maia
    </p>
  </div>
</template>
