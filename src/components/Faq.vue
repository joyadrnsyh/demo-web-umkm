<script setup>
import { ref } from 'vue'

const activeIndex = ref(null)

const faqs = [
  {
    q: 'Bagaimana sistem antar-jemput motor gratisnya?',
    a: 'Kami menyediakan pengantaran dan penjemputan gratis untuk stasiun kereta (Tugu & Lempuyangan) serta hotel/penginapan yang berada dalam radius kota Yogyakarta dengan minimal durasi sewa 3 hari. Untuk sewa di bawah 3 hari dikenakan biaya administrasi kirim flat Rp 25.000 saja.'
  },
  {
    q: 'Apa saja kelengkapan fasilitas sewa yang didapat?',
    a: 'Setiap unit sewa sudah dilengkapi dengan 2 Helm SNI bersih, wangi & steril, serta 2 jas hujan ponco berkualitas tebal. Kami juga menyediakan Phone Holder untuk GPS handphone secara gratis sesuai dengan permintaan sewa Anda.'
  },
  {
    q: 'Bagaimana jika terjadi kendala pada motor di jalan?',
    a: 'Jika terjadi kendala teknis (ban bocor, mogok, dll) di jalan, segera hubungi customer service kami. Tim operasional siaga kami akan langsung meluncur ke lokasi Anda untuk melakukan perbaikan di tempat atau mengganti unit motor cadangan agar perjalanan Anda tidak terganggu.'
  },
  {
    q: 'Apakah bensin harus diisi penuh saat pengembalian?',
    a: 'Saat serah terima unit, bensin dalam kondisi terisi (biasanya minimal 1-2 bar). Saat pengembalian, Anda cukup mengembalikan motor dengan jumlah bensin yang setara atau wajar saat motor pertama kali diterima.'
  }
]

const toggleFaq = (index) => {
  if (activeIndex.value === index) {
    activeIndex.value = null
  } else {
    activeIndex.value = index
  }
}
</script>

<template>
  <section id="faq" class="py-20 bg-white">
    <div class="max-w-4xl mx-auto px-4 sm:px-6">
      
      <!-- Header -->
      <div class="text-center mb-16 reveal reveal-up">
        <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">FAQ</span>
        <h2 class="font-heading font-extrabold text-3xl text-stone-900 mt-2">
          Pertanyaan Umum (FAQ)
        </h2>
        <p class="text-stone-600 mt-3 text-sm sm:text-base">
          Masih ragu? Berikut adalah jawaban dari beberapa pertanyaan umum seputar rental motor kami.
        </p>
      </div>

      <!-- Accordion List -->
      <div class="space-y-4">
        <div
          v-for="(faq, i) in faqs"
          :key="i"
          :class="[
            'faq-item bg-stone-50 border border-stone-200/70 rounded-2xl overflow-hidden transition-all duration-300',
            activeIndex === i ? 'active border-brand-500 bg-brand-50/5 shadow-sm' : ''
          ]"
        >
          <button
            type="button"
            @click="toggleFaq(i)"
            class="faq-header w-full px-6 py-5 text-left font-heading font-bold text-base text-stone-900 flex justify-between items-center focus:outline-none"
          >
            <span>{{ faq.q }}</span>
            <svg
              :class="[
                'w-4 h-4 text-stone-400 transition-transform duration-300 shrink-0 ml-4',
                activeIndex === i ? 'rotate-180 text-brand-600' : ''
              ]"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <polyline points="6 9 12 15 18 9"></polyline>
            </svg>
          </button>
          
          <transition
            enter-active-class="transition-all duration-300 ease-out"
            leave-active-class="transition-all duration-200 ease-in"
            enter-from-class="max-h-0 opacity-0"
            enter-to-class="max-h-96 opacity-100"
            leave-from-class="max-h-96 opacity-100"
            leave-to-class="max-h-0 opacity-0"
          >
            <div v-show="activeIndex === i" class="overflow-hidden">
              <div class="px-6 pb-5 text-stone-600 text-sm leading-relaxed border-t border-stone-200/40 pt-3">
                {{ faq.a }}
              </div>
            </div>
          </transition>
        </div>
      </div>

    </div>
  </section>
</template>
