<script setup>
import { ref, onMounted } from 'vue'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import Features from './components/Features.vue'
import FleetCatalog from './components/FleetCatalog.vue'
import Calculator from './components/Calculator.vue'
import Requirements from './components/Requirements.vue'
import Routes from './components/Routes.vue'
import Testimonials from './components/Testimonials.vue'
import Faq from './components/Faq.vue'
import Location from './components/Location.vue'
import Footer from './components/Footer.vue'
import FloatingWhatsapp from './components/FloatingWhatsapp.vue'

const activeBikeId = ref('honda-scoopy')

const handleSelectBike = (bikeId) => {
  activeBikeId.value = bikeId
  
  // Scroll smoothly to calculator section
  const calcSection = document.getElementById('kalkulator')
  if (calcSection) {
    calcSection.scrollIntoView({ behavior: 'smooth' })
    
    // Highlight the selected bike input in calculator
    const selectEl = document.getElementById('calc-bike')
    if (selectEl) {
      selectEl.classList.add('ring-4', 'ring-brand-400/50')
      setTimeout(() => {
        selectEl.classList.remove('ring-4', 'ring-brand-400/50')
      }, 1500)
    }
  }
}

onMounted(() => {
  // Intersection Observer for scroll reveal animations
  const observerOptions = {
    root: null,
    rootMargin: '0px',
    threshold: 0.1
  }

  const revealObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('revealed')
        observer.unobserve(entry.target) // Trigger animation once
      }
    })
  }, observerOptions)

  // Target all reveal elements
  const revealElements = document.querySelectorAll('.reveal, .reveal-stagger')
  revealElements.forEach(el => {
    revealObserver.observe(el)
  })
})
</script>

<template>
  <div class="font-sans antialiased text-stone-900 bg-stone-50 min-h-screen selection:bg-brand-500 selection:text-white">
    <!-- Navbar Navigation Header -->
    <Navbar />

    <main>
      <!-- Hero Section -->
      <Hero />

      <!-- Core Features / USPs Section -->
      <Features />

      <!-- Catalog Section -->
      <FleetCatalog @select-bike="handleSelectBike" />

      <!-- Calculator & Booking Form Section -->
      <Calculator :initialBikeId="activeBikeId" />

      <!-- Requirements and How-to Section -->
      <Requirements />

      <!-- Destination Routes Recommendation Section -->
      <Routes @select-bike="handleSelectBike" />

      <!-- Testimonials Ulasan Section -->
      <Testimonials />

      <!-- FAQ Accordion List Section -->
      <Faq />

      <!-- Office Location details & Map Embed Section -->
      <Location />
    </main>

    <!-- Footer Area -->
    <Footer />

    <!-- Bottom-right WhatsApp Floating Button -->
    <FloatingWhatsapp />
  </div>
</template>

<style>
/* Any global component transition styles can reside here if necessary */
</style>
