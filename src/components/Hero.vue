<script setup>
// Props or emits can be added if we want to pass search values
</script>

<template>
  <section
    id="home"
    class="relative min-h-screen flex items-center justify-start bg-cover bg-center overflow-hidden pt-32 pb-16 lg:pt-40 lg:pb-24"
    style="background-image: url('/assets/hero_bg_prambanan.png');"
  >
    <!-- Light Sand Gradient Overlay -->
    <div class="absolute inset-0 bg-gradient-to-r from-stone-50/95 via-stone-50/90 to-stone-50/40 md:to-stone-50/20 z-0"></div>

    <!-- Subtle Grid Texture -->
    <div class="absolute inset-0 bg-white/5 z-0"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 w-full grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
      <!-- Text content -->
      <div class="lg:col-span-7 flex flex-col space-y-6 text-left reveal reveal-up active">
        <!-- Green Label: 📍 RENTAL MOTOR JOGJA -->
        <div class="flex items-center space-x-2 text-brand-600 font-bold text-xs sm:text-sm tracking-widest uppercase">
          <svg class="w-4 h-4 fill-current text-brand-600 shrink-0" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd" d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z" clip-rule="evenodd" />
          </svg>
          <span>Rental Motor Jogja</span>
        </div>

        <!-- Heading H1: Sewa Motor di Jogja Mudah, Cepat, & Aman -->
        <h1 class="font-heading font-black text-4xl sm:text-5xl lg:text-6xl text-stone-900 leading-tight">
          Sewa Motor di Jogja <br />
          Mudah, Cepat, <span class="text-brand-500">&amp; Aman</span>
        </h1>

        <!-- Description -->
        <p class="text-stone-600 text-sm sm:text-base lg:text-lg max-w-xl font-normal leading-relaxed">
          Temukan pengalaman terbaik menjelajah Jogja dengan motor pilihan dan harga bersahabat. Gratis antar-jemput stasiun Tugu, Lempuyangan, dan hotel di area kota!
        </p>

        <!-- CTAs -->
        <div class="flex flex-wrap gap-4 pt-2">
          <a
            href="#armada"
            class="book-btn inline-flex items-center justify-center px-6 py-3.5 rounded-full font-heading font-bold text-sm text-stone-950 bg-brand-400 hover:bg-brand-500 transition-all duration-200 shadow-md shadow-brand-500/10"
          >
            Lihat Pilihan Motor
          </a>
          <a
            href="#kalkulator"
            class="inline-flex items-center justify-center px-6 py-3.5 rounded-full font-heading font-bold text-sm text-stone-800 bg-white hover:bg-stone-100 border border-stone-200 transition-colors shadow-sm"
          >
            Hitung Tarif
          </a>
        </div>

        <!-- USPs Row (3 Columns) -->
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-6 pt-6 border-t border-stone-200/60 mt-8">
          <!-- USP 1: Motor Terawat -->
          <div class="flex items-center space-x-3">
            <div class="text-brand-500 shrink-0">
              <svg class="w-7 h-7 stroke-current fill-none" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" />
              </svg>
            </div>
            <div>
              <h4 class="font-bold text-stone-900 text-sm sm:text-base leading-tight">Motor Terawat</h4>
              <p class="text-stone-500 text-xs mt-0.5">Bersih &amp; prima</p>
            </div>
          </div>

          <!-- USP 2: Helm & Jas Hujan -->
          <div class="flex items-center space-x-3">
            <div class="text-brand-500 shrink-0">
              <svg class="w-7 h-7 stroke-current fill-none" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <rect x="3" y="11" width="18" height="11" rx="2" ry="2" />
                <path d="M7 11V7a5 5 0 0 1 10 0v4" />
              </svg>
            </div>
            <div>
              <h4 class="font-bold text-stone-900 text-sm sm:text-base leading-tight">Fasilitas Lengkap</h4>
              <p class="text-stone-500 text-xs mt-0.5">2 Helm + Jas Hujan</p>
            </div>
          </div>

          <!-- USP 3: Antar Jemput -->
          <div class="flex items-center space-x-3">
            <div class="text-brand-500 shrink-0">
              <svg class="w-7 h-7 stroke-current fill-none" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <rect x="1" y="3" width="15" height="13" />
                <polygon points="16 8 20 8 23 11 23 16 16 16 16 8" />
                <circle cx="5.5" cy="18.5" r="2.5" />
                <circle cx="18.5" cy="18.5" r="2.5" />
              </svg>
            </div>
            <div>
              <h4 class="font-bold text-stone-900 text-sm sm:text-base leading-tight">Antar-Jemput</h4>
              <p class="text-stone-500 text-xs mt-0.5">Gratis stasiun/hotel</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
