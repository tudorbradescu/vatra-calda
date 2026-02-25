<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
  direction: {
    type: String,
    default: 'up',
    validator: (v) => ['up', 'left', 'right'].includes(v)
  },
  delay: {
    type: Number,
    default: 0
  }
})

const el = ref(null)
const isVisible = ref(false)

const animationMap = {
  up: 'fade-in-up',
  left: 'fade-in-left',
  right: 'fade-in-right'
}

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        isVisible.value = true
        observer.disconnect()
      }
    },
    { threshold: 0.1 }
  )
  if (el.value) observer.observe(el.value)
})
</script>

<template>
  <div
    ref="el"
    :style="{
      opacity: isVisible ? 1 : 0,
      animation: isVisible ? `${animationMap[direction]} 0.7s cubic-bezier(0.16, 1, 0.3, 1) ${delay}ms both` : 'none'
    }"
  >
    <slot />
  </div>
</template>
