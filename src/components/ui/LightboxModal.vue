<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'

const props = defineProps({
  images: { type: Array, required: true },
  startIndex: { type: Number, default: 0 },
})

const emit = defineEmits(['close'])

const currentIndex = ref(props.startIndex)
const transitioning = ref(false)

const currentImage = computed(() => props.images[currentIndex.value])
const counter = computed(() => `${currentIndex.value + 1} / ${props.images.length}`)

function next() {
  if (transitioning.value) return
  transitioning.value = true
  currentIndex.value = (currentIndex.value + 1) % props.images.length
  setTimeout(() => { transitioning.value = false }, 300)
}

function prev() {
  if (transitioning.value) return
  transitioning.value = true
  currentIndex.value = (currentIndex.value - 1 + props.images.length) % props.images.length
  setTimeout(() => { transitioning.value = false }, 300)
}

function close() {
  emit('close')
}

function onKeydown(e) {
  if (e.key === 'Escape') close()
  if (e.key === 'ArrowRight') next()
  if (e.key === 'ArrowLeft') prev()
}

let touchStartX = 0
let touchStartY = 0

function onTouchStart(e) {
  touchStartX = e.touches[0].clientX
  touchStartY = e.touches[0].clientY
}

function onTouchEnd(e) {
  const dx = e.changedTouches[0].clientX - touchStartX
  const dy = e.changedTouches[0].clientY - touchStartY
  if (Math.abs(dx) > Math.abs(dy) && Math.abs(dx) > 50) {
    if (dx < 0) next()
    else prev()
  }
}

onMounted(() => {
  document.addEventListener('keydown', onKeydown)
  document.body.style.overflow = 'hidden'
})

onUnmounted(() => {
  document.removeEventListener('keydown', onKeydown)
  document.body.style.overflow = ''
})
</script>

<template>
  <Teleport to="body">
    <div
      class="lightbox"
      role="dialog"
      aria-modal="true"
      aria-label="Galerie foto"
      @click.self="close"
      @touchstart="onTouchStart"
      @touchend="onTouchEnd"
    >
      <button class="lightbox-close" @click="close" aria-label="Inchide">&times;</button>
      <button class="lightbox-prev" @click="prev" aria-label="Imaginea anterioara">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="15 18 9 12 15 6"/></svg>
      </button>
      <button class="lightbox-next" @click="next" aria-label="Imaginea urmatoare">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="9 18 15 12 9 6"/></svg>
      </button>
      <div class="lightbox-content">
        <Transition name="lightbox-fade" mode="out-in">
          <img :key="currentImage.src" class="lightbox-img" :src="currentImage.src" :alt="currentImage.alt" />
        </Transition>
      </div>
      <div class="lightbox-counter">{{ counter }}</div>
    </div>
  </Teleport>
</template>
