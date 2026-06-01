<script setup>
const emit = defineEmits(['select-bike'])

const routes = [
  {
    title: 'Rute City Tour & Kuliner',
    destinations: 'Malioboro - Keraton - Taman Sari - Alun-Alun Kidul - Kulineran Kota',
    terrain: 'Datar / Perkotaan Padat',
    recommend: 'Honda Scoopy / Beat',
    bikeId: 'honda-scoopy',
    bgClass: 'bg-emerald-50/10 hover:border-emerald-300'
  },
  {
    title: 'Rute Candi & Tebing Breksi',
    destinations: 'Candi Prambanan - Tebing Breksi - Candi Ijo - Obelix Hills',
    terrain: 'Jalan Menanjak & Berkelok',
    recommend: 'Honda Vario 160 / Aerox',
    bikeId: 'honda-vario-160',
    bgClass: 'bg-amber-50/10 hover:border-amber-300'
  },
  {
    title: 'Rute Alam Kaliurang / Merapi',
    destinations: 'Kaliurang Park - Kopi Merapi - Stonehenge - Jeep Lava Tour',
    terrain: 'Pegunungan / Menanjak Dingin',
    recommend: 'Kawasaki W175 / Vespa',
    bikeId: 'kawasaki-w175',
    bgClass: 'bg-rose-50/10 hover:border-rose-300'
  },
  {
    title: 'Rute Pantai Selatan Gunungkidul',
    destinations: 'Pantai Indrayanti - Pantai Drini - Pantai Sadranan - HeHa Ocean View',
    terrain: 'Perjalanan Jauh (2-3 Jam)',
    recommend: 'Yamaha NMAX / Aerox',
    bikeId: 'yamaha-nmax',
    bgClass: 'bg-blue-50/10 hover:border-blue-300'
  }
]

const selectRecommendedBike = (bikeId) => {
  emit('select-bike', bikeId)
}
</script>

<template>
  <section id="wisata" class="py-20 bg-white border-t border-stone-200/50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Header -->
      <div class="text-center max-w-3xl mx-auto mb-16 reveal reveal-up">
        <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">Rute Rekomendasi</span>
        <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-stone-900 mt-2">
          Rekomendasi Rute &amp; Motor Terbaik
        </h2>
        <p class="text-stone-600 mt-3 text-sm sm:text-base">
          Ingin menjelajah Jogja tapi bingung rute dan motor yang cocok? Berikut rekomendasi perjalanan seru sesuai karakter medan dan pilihan armada terbaik kami.
        </p>
      </div>

      <!-- Route Cards Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8 reveal-stagger">
        <div
          v-for="(r, idx) in routes"
          :key="idx"
          :class="[
            'p-6 sm:p-8 rounded-3xl border border-stone-200/60 transition-all duration-300 flex flex-col justify-between shadow-sm hover:shadow-lg',
            r.bgClass
          ]"
        >
          <div class="space-y-4">
            <!-- Header Info -->
            <div class="flex items-center justify-between">
              <span class="px-3.5 py-1 rounded-full text-[10px] font-bold bg-stone-900 text-white uppercase tracking-wider">
                {{ r.terrain }}
              </span>
            </div>

            <!-- Route Details -->
            <h3 class="font-heading font-extrabold text-xl text-stone-950">{{ r.title }}</h3>
            
            <div class="space-y-2 text-sm text-stone-600">
              <p class="flex items-start">
                <span class="font-bold text-stone-900 mr-2 shrink-0">📍 Destinasi:</span>
                <span>{{ r.destinations }}</span>
              </p>
              <p class="flex items-center">
                <span class="font-bold text-stone-900 mr-2 shrink-0">🏍️ Rekomendasi Motor:</span>
                <span class="text-brand-600 font-bold">{{ r.recommend }}</span>
              </p>
            </div>
          </div>

          <!-- Select CTA -->
          <div class="pt-6 mt-6 border-t border-stone-100 flex items-center justify-between">
            <span class="text-xs text-stone-500 font-medium">Klik untuk pasang motor ini di kalkulator</span>
            <button
              type="button"
              @click="selectRecommendedBike(r.bikeId)"
              class="book-btn inline-flex items-center px-4 py-2.5 rounded-full font-heading font-bold text-xs text-stone-950 bg-brand-400 hover:bg-brand-500 active:scale-95 transition-all duration-200"
            >
              Sewa Motor Ini
            </button>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
