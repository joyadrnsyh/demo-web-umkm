<script setup>
const testimonials = [
  {
    name: 'M. Syarif',
    role: 'Mahasiswa UGM Jogja',
    initials: 'MS',
    rating: 5,
    text: 'Sebagai mahasiswa baru di UGM yang belum punya kendaraan, JogjaRide andalan banget kalau ada acara kelompok atau mau jalan-jalan akhir pekan. Syarat KTM doang gampang banget, dikasih kelengkapan helm bersih juga. Terima kasih JogjaRide!'
  },
  {
    name: 'Aditia Permana',
    role: 'Wisatawan Asal Jakarta',
    initials: 'AP',
    rating: 5,
    text: 'Sewa NMAX 4 hari selama liburan keluarga di Jogja. Pelayanannya luar biasa! Motor diantarkan tepat waktu ke Stasiun Tugu pas saya baru turun kereta, dan diambil lagi pas saya mau pulang. Motornya bersih wangi, jas hujan juga bersih. Recommended!'
  },
  {
    name: 'Kadek Dwipayana',
    role: 'Backpacker Asal Bali',
    initials: 'KD',
    rating: 5,
    text: 'Bawa W175 keliling Gunungkidul dan Kaliurang seru abis. Mesin sehat walafiat, tarikannya enteng, dan motornya estetik banget untuk foto-foto. CS WhatsApp-nya juga sangat ramah dan responsif saat saya butuh info rute jalan. Bintang lima!'
  }
]
</script>

<template>
  <section id="testimoni" class="py-20 bg-stone-50 border-t border-stone-200/50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Header -->
      <div class="text-center max-w-3xl mx-auto mb-16 reveal reveal-up">
        <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">Testimoni Pelanggan</span>
        <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-stone-900 mt-2">
          Apa Kata Mereka?
        </h2>
        <p class="text-stone-600 mt-3 text-sm sm:text-base">
          Lebih dari ribuan pelanggan puas menikmati perjalanan seru mereka di Yogyakarta bersama JogjaRide. Berikut beberapa ulasan jujur dari mereka.
        </p>
      </div>

      <!-- Grid Testimonials -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8 reveal-stagger">
        <div
          v-for="(t, idx) in testimonials"
          :key="idx"
          class="bg-white rounded-3xl p-6 sm:p-8 border border-stone-200/50 hover:border-brand-200 hover:shadow-lg transition-all duration-300 flex flex-col justify-between"
        >
          <div>
            <!-- Star Ratings -->
            <div class="flex items-center space-x-1 mb-4">
              <svg
                v-for="star in t.rating"
                :key="star"
                class="w-4 h-4 fill-current text-amber-500"
                viewBox="0 0 20 20"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
              </svg>
            </div>

            <!-- Review Text -->
            <p class="text-stone-600 text-sm leading-relaxed italic">
              "{{ t.text }}"
            </p>
          </div>

          <!-- Profile Info -->
          <div class="flex items-center space-x-3 mt-6 pt-6 border-t border-stone-100">
            <div class="w-10 h-10 rounded-full bg-brand-100 text-brand-800 flex items-center justify-center font-bold text-sm">
              {{ t.initials }}
            </div>
            <div>
              <h4 class="font-bold text-sm text-stone-900 leading-tight">{{ t.name }}</h4>
              <p class="text-[10px] text-stone-500 mt-0.5">{{ t.role }}</p>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
