<script setup>
import { ref, computed } from 'vue'

const emit = defineEmits(['select-bike'])

const activeFilter = ref('all')

const categories = [
  { id: 'all', name: 'Semua' },
  { id: 'matic', name: 'Matic' },
  { id: 'vespa', name: 'Vespa Retro' },
  { id: 'sport', name: 'Sport / Manual' }
]

const bikes = [
  {
    id: 'honda-beat',
    name: 'Honda Beat FI 110cc',
    price: 75000,
    category: 'matic',
    desc: '110cc | Compact Matic | Tahun 2023 - 2024',
    img: '/assets/bike_beat.png',
    ready: true,
    promo: 'Terlaris',
    specs: ['Super Irit (60km/L)', 'Lincah & Ringan', 'Bagasi Praktis', 'Pengaman Magnet']
  },
  {
    id: 'honda-scoopy',
    name: 'Honda Scoopy Prestige',
    price: 80000,
    category: 'matic',
    desc: '110cc | Retro Matic | Tahun 2023 - 2024',
    img: '/assets/bike_scoopy.png',
    ready: true,
    promo: 'Pilihan Estetis',
    specs: ['Keyless / Smart Key', 'Desain Retro Modern', 'Power Charger USB', 'Idling Stop System']
  },
  {
    id: 'honda-vario-125',
    name: 'Honda Vario 125cc CBS',
    price: 90000,
    category: 'matic',
    desc: '125cc | Daily Matic | Tahun 2023 - 2024',
    img: '/assets/bike_vario.png', // Fallback or shares image style with vario
    ready: true,
    promo: 'Paling Stabil',
    specs: ['Mesin 125cc Mantap', 'Lampu Full LED', 'Bagasi Luas 18L', 'Double Inner Pocket']
  },
  {
    id: 'honda-vario-160',
    name: 'Honda Vario 160cc ABS',
    price: 110000,
    category: 'matic',
    desc: '160cc | Sporty Matic | Tahun 2023 - 2024',
    img: '/assets/bike_vario.png',
    ready: true,
    promo: 'Mesin Bertenaga',
    specs: ['Mesin eSP+ 160cc', 'Rem ABS Safety', 'Ban Lebar Tubeless', 'Desain Dek Rata']
  },
  {
    id: 'yamaha-nmax',
    name: 'Yamaha NMAX Connected',
    price: 130000,
    category: 'matic',
    desc: '155cc | Maxi Matic | Tahun 2023 - 2024',
    img: '/assets/bike_nmax.png',
    ready: true,
    promo: 'Pilihan Nyaman',
    specs: ['Posisi Duduk Santai', 'Keyless / Y-Connect', 'Traction Control', 'Bagasi Sangat Besar']
  },
  {
    id: 'yamaha-aerox',
    name: 'Yamaha Aerox Cyber 155',
    price: 130000,
    category: 'matic',
    desc: '155cc | Sporty Maxi | Tahun 2023 - 2024',
    img: '/assets/bike_aerox.png',
    ready: true,
    promo: 'Gaya Sporty',
    specs: ['Mesin VVA 155cc', 'Desain Aerodinamis', 'Suspensi Sub-Tank', 'Spidometer Digital']
  },
  {
    id: 'vespa-sprint',
    name: 'Vespa Sprint 150 I-Get',
    price: 200000,
    category: 'vespa',
    desc: '150cc | Italian Classic | Tahun 2022 - 2023',
    img: '/assets/bike_vespa.png',
    ready: true,
    promo: 'Premium Class',
    specs: ['Mesin i-Get Halus', 'Desain Mewah Italia', 'Body Besi Kokoh', 'Sorotan Lampu Hexagonal']
  },
  {
    id: 'kawasaki-w175',
    name: 'Kawasaki W175 Cafe',
    price: 150000,
    category: 'sport',
    desc: '175cc | Retro Cafe Racer | Tahun 2022 - 2023',
    img: '/assets/bike_w175.png',
    ready: true,
    promo: 'Gaya Klasik',
    specs: ['Kopling Manual', 'Tampilan Retro Cafe', 'Suara Knalpot Khas', 'Posisi Riding Tegak']
  }
]

const filteredBikes = computed(() => {
  if (activeFilter.value === 'all') {
    return bikes
  }
  return bikes.filter(bike => bike.category === activeFilter.value)
})

const selectFilter = (filterId) => {
  activeFilter.value = filterId
}

const selectBike = (bikeId) => {
  emit('select-bike', bikeId)
}

const formatPrice = (value) => {
  return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', minimumFractionDigits: 0 }).format(value)
}
</script>

<template>
  <section id="armada" class="py-20 bg-stone-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="flex flex-col md:flex-row md:items-end justify-between mb-12 gap-6 reveal reveal-up">
        <div class="max-w-xl">
          <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">Katalog Unit</span>
          <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-stone-900 mt-2">
            Pilih Armada Terbaik Anda
          </h2>
          <p class="text-stone-600 mt-2 text-sm sm:text-base">
            Mulai dari motor matic lincah, retro bernuansa estetis, hingga motor sport tangguh untuk menjelajahi alam Jogja.
          </p>
        </div>

        <!-- Category Filter Tabs -->
        <div class="flex flex-wrap gap-2">
          <button
            v-for="cat in categories"
            :key="cat.id"
            type="button"
            @click="selectFilter(cat.id)"
            :class="[
              'px-5 py-2.5 rounded-full font-semibold text-sm transition-all duration-300 active:scale-95 border',
              activeFilter === cat.id
                ? 'bg-brand-500 text-white shadow-md shadow-brand-500/20 border-brand-500'
                : 'bg-white text-stone-700 border-stone-200 hover:border-brand-200'
            ]"
          >
            {{ cat.name }}
          </button>
        </div>
      </div>

      <!-- Fleet Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 reveal-stagger">
        <div
          v-for="bike in filteredBikes"
          :key="bike.id"
          class="fleet-card bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl border border-stone-200/50 hover:border-brand-200 transition-all duration-300 flex flex-col justify-between"
        >
          <div>
            <!-- Image Frame -->
            <div class="relative h-48 overflow-hidden bg-stone-100 flex items-center justify-center p-4">
              <img
                :src="bike.img"
                :alt="bike.name"
                class="w-full h-full object-contain hover:scale-105 transition-transform duration-300"
              />
              <span
                v-if="bike.ready"
                class="absolute top-3 right-3 px-2.5 py-1 rounded-full text-[10px] font-bold bg-emerald-500 text-white uppercase tracking-wider shadow-sm"
              >
                Ready
              </span>
              <span
                v-if="bike.promo"
                class="absolute top-3 left-3 px-2.5 py-1 rounded-full text-[10px] font-bold bg-brand-100 text-brand-800 tracking-wide uppercase"
              >
                {{ bike.promo }}
              </span>
            </div>

            <!-- Details -->
            <div class="p-5">
              <h3 class="font-heading font-bold text-base text-stone-950">{{ bike.name }}</h3>
              <p class="text-xs text-stone-500 mt-1">{{ bike.desc }}</p>

              <!-- Specs bullet points -->
              <div class="grid grid-cols-2 gap-2 mt-4 text-[11px] text-stone-600">
                <div v-for="(spec, idx) in bike.specs" :key="idx" class="flex items-center space-x-1.5">
                  <svg class="w-3.5 h-3.5 text-brand-500 shrink-0" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24">
                    <polyline points="20 6 9 17 4 12" />
                  </svg>
                  <span>{{ spec }}</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Price & CTA -->
          <div class="p-5 pt-0 border-t border-stone-100 flex items-center justify-between mt-4">
            <div>
              <p class="text-[10px] font-semibold text-stone-400 uppercase">Tarif Harian</p>
              <p class="font-heading font-extrabold text-brand-600 text-base">{{ formatPrice(bike.price) }}</p>
            </div>
            <button
              type="button"
              @click="selectBike(bike.id)"
              class="book-btn inline-flex items-center px-5 py-2.5 rounded-full font-heading font-bold text-xs text-stone-950 bg-brand-400 hover:bg-brand-500 active:scale-95 transition-all duration-200"
            >
              Sewa Motor
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
