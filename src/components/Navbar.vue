<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)

const handleScroll = () => {
  if (window.scrollY > 50) {
    isScrolled.value = true
  } else {
    isScrolled.value = false
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll() // initial check
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}
</script>

<template>
  <header
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      isScrolled 
        ? 'bg-white/90 backdrop-blur-md border-b border-stone-200/60 shadow-sm py-4' 
        : 'bg-transparent border-b border-transparent py-6'
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between">
        <!-- Logo -->
        <a href="#home" class="flex items-center space-x-2.5 focus:outline-none" @click="closeMobileMenu">
          <div class="w-9 h-9 rounded-xl bg-brand-500 flex items-center justify-center text-white font-black shadow-md shadow-brand-500/20">
          
            <span class="text-lg">JR</span>
          </div>
          <span class="font-heading font-black text-xl tracking-tight text-stone-900">
            Jogja<span class="text-brand-500">Ride</span>
          </span>
        </a>

        <!-- Desktop Navigation -->
        <nav class="hidden md:flex items-center space-x-8">
          <a href="#home" class="text-sm font-semibold text-stone-600 hover:text-brand-600 transition-colors">Beranda</a>
          <a href="#armada" class="text-sm font-semibold text-stone-600 hover:text-brand-600 transition-colors">Armada</a>
          <a href="#kalkulator" class="text-sm font-semibold text-stone-600 hover:text-brand-600 transition-colors">Kalkulator</a>
          <a href="#syarat" class="text-sm font-semibold text-stone-600 hover:text-brand-600 transition-colors">Syarat & Layanan</a>
          <a href="#wisata" class="text-sm font-semibold text-stone-600 hover:text-brand-600 transition-colors">Rute Wisata</a>
          <a href="#faq" class="text-sm font-semibold text-stone-600 hover:text-brand-600 transition-colors">FAQ</a>
          <a href="#lokasi" class="text-sm font-semibold text-stone-600 hover:text-brand-600 transition-colors">Lokasi</a>
        </nav>

        <!-- CTA Button -->
        <div class="hidden md:block">
          <a
            href="#kalkulator"
            class="book-btn inline-flex items-center justify-center px-5 py-2.5 rounded-full font-heading font-bold text-xs text-stone-950 bg-brand-400 hover:bg-brand-500 transition-all duration-200"
          >
            Pesan Sekarang
          </a>
        </div>

        <!-- Mobile Menu Button -->
        <div class="md:hidden">
          <button
            type="button"
            @click="toggleMobileMenu"
            class="p-2 rounded-xl text-stone-700 hover:bg-stone-100 focus:outline-none transition-colors"
            aria-label="Toggle Menu"
          >
            <!-- Open Icon -->
            <svg
              v-if="!mobileMenuOpen"
              class="w-6 h-6"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              stroke-width="2"
            >
              <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
            <!-- Close Icon -->
            <svg
              v-else
              class="w-6 h-6"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              stroke-width="2"
            >
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Drawer Menu -->
    <transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 translate-y-[-10px]"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 translate-y-[-10px]"
    >
      <div v-if="mobileMenuOpen" class="md:hidden absolute top-full left-0 right-0 bg-white/95 backdrop-blur-lg border-b border-stone-200 shadow-lg py-4 px-6 space-y-3 flex flex-col">
        <a href="#home" @click="closeMobileMenu" class="py-2 text-base font-semibold text-stone-800 hover:text-brand-600 transition-colors">Beranda</a>
        <a href="#armada" @click="closeMobileMenu" class="py-2 text-base font-semibold text-stone-800 hover:text-brand-600 transition-colors">Armada</a>
        <a href="#kalkulator" @click="closeMobileMenu" class="py-2 text-base font-semibold text-stone-800 hover:text-brand-600 transition-colors">Kalkulator</a>
        <a href="#syarat" @click="closeMobileMenu" class="py-2 text-base font-semibold text-stone-800 hover:text-brand-600 transition-colors">Syarat & Layanan</a>
        <a href="#wisata" @click="closeMobileMenu" class="py-2 text-base font-semibold text-stone-800 hover:text-brand-600 transition-colors">Rute Wisata</a>
        <a href="#faq" @click="closeMobileMenu" class="py-2 text-base font-semibold text-stone-800 hover:text-brand-600 transition-colors">FAQ</a>
        <a href="#lokasi" @click="closeMobileMenu" class="py-2 text-base font-semibold text-stone-800 hover:text-brand-600 transition-colors">Lokasi</a>
        <div class="pt-2 border-t border-stone-100">
          <a
            href="#kalkulator"
            @click="closeMobileMenu"
            class="book-btn w-full text-center inline-flex items-center justify-center px-5 py-3 rounded-full font-heading font-bold text-sm text-stone-950 bg-brand-400 hover:bg-brand-500 transition-all duration-200"
          >
            Pesan Sekarang
          </a>
        </div>
      </div>
    </transition>
  </header>
</template>
