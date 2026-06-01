<script setup>
const documents = [
  { name: 'E-KTP (Wajib)', desc: 'Kartu Tanda Penduduk asli dari penyewa.' },
  { name: 'KTM / Kartu Pelajar', desc: 'Kartu Tanda Mahasiswa yang masih aktif.' },
  { name: 'SIM A / C', desc: 'Surat Izin Mengemudi mobil atau motor.' },
  { name: 'Paspor', desc: 'Untuk wisatawan asing / lokal.' },
  { name: 'Kartu Keluarga (KK)', desc: 'Foto KK asli atau fotokopi jelas.' },
  { name: 'BPJS / KIS', desc: 'Kartu jaminan kesehatan nasional.' },
  { name: 'NPWP', desc: 'Nomor Pokok Wajib Pajak.' }
]

const steps = [
  {
    num: 1,
    title: 'Hubungi & Pesan',
    desc: 'Gunakan kalkulator tarif di atas untuk memilih motor favorit Anda dan menghitung biayanya secara langsung.'
  },
  {
    num: 2,
    title: 'Verifikasi Cepat',
    desc: 'Kirimkan foto 2 jenis dokumen penjamin yang valid via chat WhatsApp untuk divalidasi dengan cepat oleh tim admin.'
  },
  {
    num: 3,
    title: 'Antar Unit',
    desc: 'Tim delivery kami akan mengantarkan motor langsung ke Stasiun, Hotel, atau titik yang disepakati lengkap dengan helm dan jas hujan.'
  },
  {
    num: 4,
    title: 'Jelajahi Jogja!',
    desc: 'Motor siap dikendarai. Nikmati perjalanan liburan Anda di Jogja, lalu kembalikan unit di titik kesepakatan akhir.'
  }
]
</script>

<template>
  <section id="syarat" class="py-20 bg-stone-50 border-t border-stone-200/50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-start">
        
        <!-- Left: Requirements Info -->
        <div class="lg:col-span-6 flex flex-col space-y-6 reveal reveal-left">
          <div>
            <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">Persyaratan Mudah</span>
            <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-stone-900 mt-2">
              Syarat Sewa Motor Jogja
            </h2>
            <p class="text-stone-600 mt-3 text-sm sm:text-base leading-relaxed">
              Kami tidak mempersulit Anda. Cukup siapkan minimal <span class="font-bold text-stone-900">2 jenis identitas asli</span> yang masih berlaku untuk disimpan sebagai jaminan selama masa rental (tanpa deposit uang).
            </p>
          </div>

          <!-- Document Grid List -->
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-2">
            <div
              v-for="(doc, idx) in documents"
              :key="idx"
              class="p-4 bg-white rounded-2xl border border-stone-200/60 shadow-sm flex items-start space-x-3"
            >
              <div class="text-brand-600 shrink-0 mt-0.5">
                <svg class="w-5 h-5 fill-current" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
              </div>
              <div>
                <h4 class="font-bold text-stone-900 text-sm leading-tight">{{ doc.name }}</h4>
                <p class="text-stone-500 text-xs mt-0.5 leading-relaxed">{{ doc.desc }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Step Workflow Timeline -->
        <div class="lg:col-span-6 flex flex-col space-y-8 reveal reveal-right">
          <div>
            <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">Cara Pemesanan</span>
            <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-stone-900 mt-2">
              4 Langkah Mudah Sewa
            </h2>
            <p class="text-stone-600 mt-3 text-sm sm:text-base leading-relaxed">
              Proses booking hingga serah terima motor dilakukan dengan sangat cepat dan fleksibel secara online.
            </p>
          </div>

          <!-- Timeline -->
          <div class="relative pl-6 border-l-2 border-stone-200 space-y-8 ml-4">
            <div
              v-for="step in steps"
              :key="step.num"
              class="relative flex flex-col sm:flex-row items-start sm:items-center gap-4"
            >
              <!-- Timeline node dot -->
              <div class="absolute -left-[39px] w-8 h-8 rounded-full bg-brand-400 border-4 border-stone-50 text-stone-950 flex items-center justify-center font-heading font-extrabold text-xs shadow-md">
                {{ step.num }}
              </div>
              
              <!-- Content -->
              <div class="bg-white p-5 rounded-2xl border border-stone-200/60 shadow-sm w-full">
                <h4 class="font-bold text-stone-900 text-sm leading-tight">{{ step.title }}</h4>
                <p class="text-stone-600 text-xs leading-relaxed mt-1.5">{{ step.desc }}</p>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>
