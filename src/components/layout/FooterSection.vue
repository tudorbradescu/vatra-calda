<script setup>
import { Phone, MapPin, Facebook, Clock } from 'lucide-vue-next'
</script>

<template>
  <footer class="bg-surface-secondary border-t border-border-subtle">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-10">
        <!-- Brand -->
        <div>
          <div class="mb-4">
            <span class="font-heading text-2xl font-bold text-text-primary">Vatra </span>
            <span class="font-heading text-2xl font-bold text-brand">Calda</span>
          </div>
          <p class="font-heading italic text-text-secondary mb-4">arta painii cu maia</p>
          <p class="text-text-muted text-sm">
            Brutarie artizanala in Arad. Paine cu maia, croissante si patiserie coapte cu pasiune.
          </p>
        </div>

        <!-- Navigare -->
        <div>
          <h3 class="font-heading font-bold text-text-primary mb-4">Navigare</h3>
          <ul class="space-y-2">
            <li><a href="#despre" class="text-text-secondary hover:text-brand transition-colors text-sm">Povestea Noastra</a></li>
            <li><a href="#meniu" class="text-text-secondary hover:text-brand transition-colors text-sm">Meniu</a></li>
            <li><a href="#program" class="text-text-secondary hover:text-brand transition-colors text-sm">Program Paine</a></li>
            <li><a href="#galerie" class="text-text-secondary hover:text-brand transition-colors text-sm">Galerie</a></li>
            <li><a href="#contact" class="text-text-secondary hover:text-brand transition-colors text-sm">Contact</a></li>
          </ul>
        </div>

        <!-- Produse -->
        <div>
          <h3 class="font-heading font-bold text-text-primary mb-4">Produse</h3>
          <ul class="space-y-2">
            <li class="text-text-secondary text-sm">Paine cu Maia</li>
            <li class="text-text-secondary text-sm">Croissante</li>
            <li class="text-text-secondary text-sm">Patiserie Dulce</li>
            <li class="text-text-secondary text-sm">Specialitati Sarate</li>
            <li class="text-text-secondary text-sm">Tarte</li>
          </ul>
        </div>

        <!-- Contact -->
        <div>
          <h3 class="font-heading font-bold text-text-primary mb-4">Contact</h3>
          <ul class="space-y-3">
            <li>
              <a href="tel:0754696028" class="flex items-center gap-2 text-brand hover:text-brand-light transition-colors text-sm font-semibold">
                <Phone :size="16" />
                0754 696 028
              </a>
            </li>
            <li class="flex items-start gap-2 text-text-secondary text-sm">
              <MapPin :size="16" class="shrink-0 mt-0.5" />
              <span>Calea Timisoarei 55, Arad</span>
            </li>
            <li class="flex items-center gap-2 text-text-secondary text-sm">
              <Clock :size="16" class="shrink-0" />
              <span>L-V: 09-17:30 | S: 09-13</span>
            </li>
            <li>
              <a
                href="https://www.facebook.com/vatracalda/"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center gap-2 text-text-secondary hover:text-brand transition-colors text-sm"
              >
                <Facebook :size="16" />
                facebook.com/vatracalda
              </a>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom bar -->
      <div class="mt-12 pt-8 border-t border-border-subtle text-center">
        <p class="text-text-muted text-sm">
          &copy; {{ new Date().getFullYear() }} Vatra Calda. Toate drepturile rezervate.
        </p>
      </div>
    </div>
  </footer>
</template>
