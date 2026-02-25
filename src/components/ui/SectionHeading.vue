<script setup>
defineProps({
  label: String,
  title: String,
  subtitle: String,
  light: { type: Boolean, default: false }
})
</script>

<template>
  <div class="text-center mb-12 lg:mb-16">
    <p
      v-if="label"
      class="text-sm font-semibold tracking-[0.2em] uppercase mb-4"
      :class="light ? 'text-brand-dark' : 'text-brand'"
    >
      {{ label }}
    </p>
    <h2
      class="font-heading text-3xl sm:text-4xl lg:text-5xl font-bold mb-4"
      :class="light ? 'text-text-dark' : 'text-text-primary'"
    >
      {{ title }}
    </h2>
    <!-- Gold ornament -->
    <div class="flex items-center justify-center gap-3 mb-6">
      <span class="block w-12 h-px" :class="light ? 'bg-brand-dark/30' : 'bg-brand/40'"></span>
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" class="text-brand">
        <path d="M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10 10-4.5 10-10S17.5 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8z" fill="currentColor" opacity="0.3"/>
        <path d="M12 6c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zm-4 8c0 2.21 1.79 4 4 4s4-1.79 4-4c0-1.1-.9-2-2-2h-4c-1.1 0-2 .9-2 2z" fill="currentColor"/>
      </svg>
      <span class="block w-12 h-px" :class="light ? 'bg-brand-dark/30' : 'bg-brand/40'"></span>
    </div>
    <p
      v-if="subtitle"
      class="text-lg max-w-2xl mx-auto"
      :class="light ? 'text-text-dark-secondary' : 'text-text-secondary'"
    >
      {{ subtitle }}
    </p>
  </div>
</template>
