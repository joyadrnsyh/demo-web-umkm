<script setup>
const features = [
  {
    title: 'Antar Jemput Gratis',
    desc: 'Layanan antar-jemput motor gratis di Stasiun Tugu, Stasiun Lempuyangan, dan hotel/penginapan radius kota (min. sewa 3 hari).',
    icon: 'M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z'
  },
  {
    title: 'Unit Prima & Bersih',
    desc: 'Semua armada diservis rutin di bengkel resmi, dicuci bersih, dan dicek kelayakan berkendaranya sebelum dikirim ke pelanggan.',
    icon: 'M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z'
  },
  {
    title: 'Fasilitas Berkendara',
    desc: 'Dilengkapi dengan 2 helm SNI bersih & wangi, 2 jas hujan berkualitas, serta phone holder (by request) untuk navigasi GPS Anda.',
    icon: 'M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z'
  },
  {
    title: 'Fast Respon & Siaga',
    desc: 'Customer support kami ramah dan tanggap membantu proses booking, serta siap melayani dan memberikan solusi kendala darurat di jalan.',
    icon: 'M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z'
  }
]
</script>

<template>
  <section id="layanan" class="py-20 bg-white border-t border-stone-200/50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Header -->
      <div class="text-center max-w-3xl mx-auto mb-16 reveal reveal-up">
        <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">Keunggulan Kami</span>
        <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-stone-900 mt-2">
          Mengapa Memilih JogjaRide?
        </h2>
        <p class="text-stone-600 mt-3 text-sm sm:text-base">
          Kami berkomitmen memberikan layanan sewa motor terbaik dengan kemudahan proses dan kualitas unit yang prima untuk kenyamanan liburan Anda di Jogja.
        </p>
      </div>

      <!-- Feature Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 reveal-stagger">
        <div
          v-for="(f, i) in features"
          :key="i"
          class="p-6 rounded-2xl border border-stone-100 hover:border-brand-200 hover:bg-brand-50/10 transition-all duration-300 flex flex-col items-start space-y-4 shadow-sm hover:shadow-md hover:-translate-y-1"
        >
          <div class="w-12 h-12 rounded-xl bg-brand-50 flex items-center justify-center text-brand-600">
            <svg class="w-6 h-6 stroke-current fill-none" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path :d="f.icon" />
            </svg>
          </div>
          <h3 class="font-heading font-bold text-lg text-stone-900">{{ f.title }}</h3>
          <p class="text-stone-600 text-sm leading-relaxed">{{ f.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
