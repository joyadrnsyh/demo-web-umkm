<script setup>
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="bg-stone-900 text-white pt-16 pb-8 border-t border-stone-850">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-12 gap-8 border-b border-stone-800 pb-12">
      
      <!-- Brand column -->
      <div class="md:col-span-5 flex flex-col space-y-4">
        <a href="#home" class="flex items-center space-x-2.5 focus:outline-none">
          <div class="w-9 h-9 rounded-xl bg-brand-500 flex items-center justify-center text-white font-black">
            <span>JR</span>
          </div>
          <span class="font-heading font-black text-xl tracking-tight text-white">
            Jogja<span class="text-brand-500">Ride</span>
          </span>
        </a>
        <p class="text-stone-400 text-xs sm:text-sm leading-relaxed max-w-sm">
          Penyedia jasa layanan rental motor murah, tepercaya, dan profesional di Yogyakarta. Gratis pengantaran stasiun kereta Tugu, Lempuyangan, dan hotel area kota.
        </p>
      </div>

      <!-- Quick links column -->
      <div class="md:col-span-3 flex flex-col space-y-3">
        <h4 class="font-heading font-bold text-sm text-white uppercase tracking-wider">Navigasi</h4>
        <ul class="space-y-2 text-xs sm:text-sm text-stone-450">
          <li><a href="#home" class="hover:text-brand-400 transition-colors">Beranda</a></li>
          <li><a href="#armada" class="hover:text-brand-400 transition-colors">Armada Motor</a></li>
          <li><a href="#kalkulator" class="hover:text-brand-400 transition-colors">Kalkulator Booking</a></li>
          <li><a href="#syarat" class="hover:text-brand-400 transition-colors">Persyaratan</a></li>
        </ul>
      </div>

      <!-- Contact column -->
      <div class="md:col-span-4 flex flex-col space-y-3">
        <h4 class="font-heading font-bold text-sm text-white uppercase tracking-wider">Hubungi Kami</h4>
        <p class="text-stone-400 text-xs sm:text-sm leading-relaxed">
          Jl. Sosrowijayan No.45, Sosromenduran, Gedong Tengen, Kota Yogyakarta
        </p>
        <p class="text-stone-400 text-xs sm:text-sm font-semibold">
          WhatsApp: <span class="text-brand-400">+62 812-2822-9221</span>
        </p>
        <p class="text-stone-450 text-[11px] uppercase tracking-wide">
          Jam Buka: 06:00 - 22:00 WIB
        </p>
      </div>

    </div>

    <!-- Copyright -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-8 flex flex-col sm:flex-row items-center justify-between text-xs text-stone-500 gap-4">
      <p>&copy; {{ currentYear }} JogjaRide Rental Motor Jogja. All Rights Reserved.</p>
      <p>Sewa Motor Jogja Murah &amp; Syarat Mudah.</p>
    </div>
  </footer>
</template>
