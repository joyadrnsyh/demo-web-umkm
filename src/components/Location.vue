<script setup>
const officeAddress = 'Jl. Sosrowijayan No.45, Sosromenduran, Gedong Tengen, Kota Yogyakarta, Daerah Istimewa Yogyakarta 55271'
const distanceInfo = '300 meter (3 menit jalan kaki) dari pintu keluar selatan Stasiun Tugu Jogja.'
const opHours = '06:00 - 22:00 WIB (Setiap Hari)'
const waContact = '+62 812-2822-9221'
</script>

<template>
  <section id="lokasi" class="py-20 bg-stone-50 border-t border-stone-200/50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
        
        <!-- Address & Contact Details -->
        <div class="lg:col-span-5 flex flex-col space-y-6 reveal reveal-left">
          <div>
            <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">Lokasi Kantor</span>
            <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-stone-900 mt-2">
              Sangat Dekat Stasiun Tugu
            </h2>
            <p class="text-stone-600 mt-3 text-sm sm:text-base leading-relaxed">
              Lokasi garasi dan kantor kami sangat strategis dan mudah dijangkau bagi Anda yang baru tiba di Yogyakarta.
            </p>
          </div>

          <div class="space-y-4">
            <!-- Address Item -->
            <div class="flex items-start space-x-3">
              <div class="text-brand-600 shrink-0 mt-1">
                <svg class="w-5 h-5 fill-none stroke-current" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z" />
                  <circle cx="12" cy="10" r="3" />
                </svg>
              </div>
              <div>
                <h4 class="font-bold text-stone-900 text-sm">Alamat Kantor</h4>
                <p class="text-stone-650 text-xs mt-1 leading-relaxed">{{ officeAddress }}</p>
                <p class="text-brand-700 text-xs font-bold mt-1">📍 {{ distanceInfo }}</p>
              </div>
            </div>

            <!-- Operating Hours -->
            <div class="flex items-start space-x-3">
              <div class="text-brand-600 shrink-0 mt-1">
                <svg class="w-5 h-5 fill-none stroke-current" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <circle cx="12" cy="12" r="10" />
                  <polyline points="12 6 12 12 16 14" />
                </svg>
              </div>
              <div>
                <h4 class="font-bold text-stone-900 text-sm">Jam Operasional</h4>
                <p class="text-stone-650 text-xs mt-1 leading-relaxed">{{ opHours }}</p>
              </div>
            </div>

            <!-- Contact -->
            <div class="flex items-start space-x-3">
              <div class="text-brand-600 shrink-0 mt-1">
                <svg class="w-5 h-5 fill-none stroke-current" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z" />
                </svg>
              </div>
              <div>
                <h4 class="font-bold text-stone-900 text-sm">Telepon / WhatsApp</h4>
                <p class="text-stone-650 text-xs mt-1 leading-relaxed">{{ waContact }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Google Maps Embed -->
        <div class="lg:col-span-7 reveal reveal-right">
          <div class="w-full h-80 sm:h-96 rounded-3xl overflow-hidden border border-stone-200 shadow-sm">
            <iframe src="https://www.google.com/maps/embed?pb=!1m14!1m12!1m3!1d9676.404886037104!2d110.38812506622816!3d-7.83136266866829!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!5e0!3m2!1sid!2sid!4v1779718140936!5m2!1sid!2sid" width="100%" height="100%" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>
