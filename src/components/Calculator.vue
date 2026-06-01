<script setup>
import { ref, computed, watch } from 'vue'

const props = defineProps({
  initialBikeId: {
    type: String,
    default: 'honda-scoopy'
  }
})

const bikeDatabase = {
  'honda-beat': { name: 'Honda Beat FI 110cc', price: 75000 },
  'honda-scoopy': { name: 'Honda Scoopy Prestige 110cc', price: 80000 },
  'honda-vario-125': { name: 'Honda Vario 125cc CBS', price: 90000 },
  'honda-vario-160': { name: 'Honda Vario 160cc ABS', price: 110000 },
  'yamaha-nmax': { name: 'Yamaha NMAX Connected 155cc', price: 130000 },
  'yamaha-aerox': { name: 'Yamaha Aerox Cyber 155cc', price: 130000 },
  'vespa-sprint': { name: 'Vespa Sprint 150 I-Get', price: 200000 },
  'kawasaki-w175': { name: 'Kawasaki W175 Cafe', price: 150000 }
}

const selectedBike = ref(props.initialBikeId)
const days = ref(3)
const addonDelivery = ref(true)
const addonHelmet = ref(false)
const addonPhoneHolder = ref(false)

// Watch for prop updates to change selected bike (from catalog click)
watch(() => props.initialBikeId, (newVal) => {
  if (newVal && bikeDatabase[newVal]) {
    selectedBike.value = newVal
  }
})

// Customer Booking Details
const name = ref('')
const phone = ref('')
const startDate = ref('')
const startTime = ref('08:00')
const deliveryLocation = ref('Stasiun Tugu')
const notes = ref('')

// Calculations
const bikeRate = computed(() => {
  return bikeDatabase[selectedBike.value]?.price || 0
})

const bikeName = computed(() => {
  return bikeDatabase[selectedBike.value]?.name || ''
})

const subtotalBike = computed(() => {
  return bikeRate.value * days.value
})

const discountPercent = computed(() => {
  if (days.value >= 7) return 0.20 // 20% discount
  if (days.value >= 3) return 0.10 // 10% discount
  return 0
})

const discountAmount = computed(() => {
  return subtotalBike.value * discountPercent.value
})

const deliveryFee = computed(() => {
  // Free delivery for rentals >= 3 days, otherwise Rp 25.000 flat
  if (!addonDelivery.value) return 0
  return days.value >= 3 ? 0 : 25000
})

const extraHelmetFee = computed(() => {
  if (!addonHelmet.value) return 0
  return 10000 * days.value // Rp 10.000 per day
})

const phoneHolderFee = computed(() => {
  if (!addonPhoneHolder.value) return 0
  return 5000 * days.value // Rp 5.000 per day
})

const totalAddons = computed(() => {
  return deliveryFee.value + extraHelmetFee.value + phoneHolderFee.value
})

const grandTotal = computed(() => {
  return subtotalBike.value - discountAmount.value + totalAddons.value
})

const formatPrice = (value) => {
  return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', minimumFractionDigits: 0 }).format(value)
}

const sendBooking = () => {
  if (!name.value || !startDate.value) {
    alert('Harap isi Nama Lengkap dan Tanggal Mulai Sewa terlebih dahulu.')
    return
  }

  const addonsList = []
  if (addonDelivery.value) addonsList.push(`Antar-Jemput (${deliveryLocation.value})`)
  if (addonHelmet.value) addonsList.push('Helm Ekstra (Total 3 Helm)')
  if (addonPhoneHolder.value) addonsList.push('Phone Holder GPS')
  
  const addonsText = addonsList.length > 0 ? addonsList.join(', ') : 'Tidak ada'

  const message = `Halo JogjaRide! Saya ingin memesan sewa motor:

- Nama: ${name.value}
- No. HP: ${phone.value || '-'}
- Unit Motor: ${bikeName.value}
- Durasi Sewa: ${days.value} Hari
- Mulai Sewa: ${startDate.value} jam ${startTime.value} WIB
- Pengantaran: ${addonDelivery.value ? deliveryLocation.value : 'Ambil di Kantor'}
- Layanan Tambahan: ${addonsText}
- Catatan Tambahan: ${notes.value || '-'}

*Estimasi Total:* ${formatPrice(grandTotal.value)}

Mohon info ketersediaan unit dan langkah selanjutnya. Terima kasih!`

  const waUrl = `https://wa.me/6281228229221?text=${encodeURIComponent(message)}`
  window.open(waUrl, '_blank')
}
</script>

<template>
  <section id="kalkulator" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Header -->
      <div class="text-center max-w-3xl mx-auto mb-16 reveal reveal-up">
        <span class="text-brand-600 font-extrabold text-sm uppercase tracking-widest">Kalkulator Tarif</span>
        <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-stone-900 mt-2">
          Hitung &amp; Pesan Online
        </h2>
        <p class="text-stone-600 mt-3 text-sm sm:text-base">
          Sesuaikan tipe motor, durasi sewa, dan layanan tambahan. Total harga langsung tampil di layar secara transparan!
        </p>
      </div>

      <!-- Main Panel Grid -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-start reveal-stagger">
        <!-- Input controls (Left column) -->
        <div class="lg:col-span-7 bg-stone-50 rounded-3xl p-6 sm:p-8 border border-stone-200/60 shadow-sm flex flex-col space-y-6">
          <h3 class="font-heading font-extrabold text-xl text-stone-950 border-b border-stone-200 pb-3">Konfigurasi Sewa</h3>

          <!-- Bike Selection -->
          <div class="flex flex-col space-y-2">
            <label for="calc-bike" class="text-sm font-bold text-stone-850">Pilih Armada</label>
            <select
              id="calc-bike"
              v-model="selectedBike"
              class="w-full bg-white border border-stone-300 rounded-xl px-4 py-3 text-sm text-stone-900 font-semibold focus:outline-none focus:border-brand-500 focus:ring-2 focus:ring-brand-200/50"
            >
              <option v-for="(val, key) in bikeDatabase" :key="key" :value="key">
                {{ val.name }} ({{ formatPrice(val.price) }} / hari)
              </option>
            </select>
          </div>

          <!-- Duration Days Slider -->
          <div class="flex flex-col space-y-2">
            <div class="flex justify-between items-center">
              <label for="calc-days" class="text-sm font-bold text-stone-850">Durasi Sewa</label>
              <span class="px-3 py-1 rounded-full text-xs font-extrabold bg-brand-100 text-brand-850">
                {{ days }} Hari
              </span>
            </div>
            <input
              type="range"
              id="calc-days"
              min="1"
              max="14"
              v-model.number="days"
              class="w-full h-2 bg-stone-200 rounded-lg appearance-none cursor-pointer accent-brand-500"
            />
            <div class="flex justify-between text-[10px] font-bold text-stone-500 mt-1 uppercase">
              <span>1 Hari</span>
              <span>3 Hari (Diskon 10%)</span>
              <span>7 Hari (Diskon 20%)</span>
              <span>14 Hari</span>
            </div>
          </div>

          <!-- Optional Addons -->
          <div class="flex flex-col space-y-3">
            <span class="text-sm font-bold text-stone-850">Layanan Tambahan (Opsional)</span>
            
            <!-- Delivery -->
            <label
              :class="[
                'flex items-start p-4 rounded-2xl border cursor-pointer transition-all duration-200 bg-white',
                addonDelivery ? 'border-brand-300 bg-brand-50/5' : 'border-stone-200'
              ]"
            >
              <input
                type="checkbox"
                v-model="addonDelivery"
                class="mt-1 w-4.5 h-4.5 text-brand-500 rounded border-stone-300 focus:ring-brand-400 accent-brand-500"
              />
              <div class="ml-3">
                <span class="block text-sm font-bold text-stone-900">Layanan Antar - Jemput Motor</span>
                <span class="block text-xs text-stone-500 mt-0.5">
                  Gratis untuk sewa ≥3 hari. Di bawah 3 hari dikenakan biaya flat Rp 25.000.
                </span>
              </div>
            </label>

            <!-- Extra Helmet -->
            <label
              :class="[
                'flex items-start p-4 rounded-2xl border cursor-pointer transition-all duration-200 bg-white',
                addonHelmet ? 'border-brand-300 bg-brand-50/5' : 'border-stone-200'
              ]"
            >
              <input
                type="checkbox"
                v-model="addonHelmet"
                class="mt-1 w-4.5 h-4.5 text-brand-500 rounded border-stone-300 focus:ring-brand-400 accent-brand-500"
              />
              <div class="ml-3">
                <span class="block text-sm font-bold text-stone-900">Helm Tambahan (Helm Ke-3)</span>
                <span class="block text-xs text-stone-500 mt-0.5">
                  Ingin boncengan bertiga atau cadangan? Sewa ekstra helm Rp 10.000 / hari. (Fasilitas gratis dapat 2 helm)
                </span>
              </div>
            </label>

            <!-- Phone Holder -->
            <label
              :class="[
                'flex items-start p-4 rounded-2xl border cursor-pointer transition-all duration-200 bg-white',
                addonPhoneHolder ? 'border-brand-300 bg-brand-50/5' : 'border-stone-200'
              ]"
            >
              <input
                type="checkbox"
                v-model="addonPhoneHolder"
                class="mt-1 w-4.5 h-4.5 text-brand-500 rounded border-stone-300 focus:ring-brand-400 accent-brand-500"
              />
              <div class="ml-3">
                <span class="block text-sm font-bold text-stone-900">Phone Holder GPS</span>
                <span class="block text-xs text-stone-500 mt-0.5">
                  Dudukan HP kokoh di stang untuk memudahkan melihat peta navigasi Google Maps. Tarif Rp 5.000 / hari.
                </span>
              </div>
            </label>
          </div>
        </div>

        <!-- Checkout / Form Panel (Right column) -->
        <div class="lg:col-span-5 flex flex-col space-y-6">
          <!-- Pricing Summary Card -->
          <div class="bg-stone-950 text-white rounded-3xl p-6 sm:p-8 shadow-xl flex flex-col space-y-4">
            <h3 class="font-heading font-extrabold text-lg text-brand-400 border-b border-white/10 pb-3">Rincian Tarif</h3>
            
            <div class="space-y-2.5 text-sm">
              <div class="flex justify-between text-stone-400">
                <span>Armada ({{ bikeRate ? formatPrice(bikeRate) : '-' }} x {{ days }} Hari)</span>
                <span class="font-mono text-white">{{ formatPrice(subtotalBike) }}</span>
              </div>
              
              <div v-if="discountPercent > 0" class="flex justify-between text-emerald-400 font-semibold">
                <span>Diskon Durasi ({{ discountPercent * 100 }}%)</span>
                <span class="font-mono">- {{ formatPrice(discountAmount) }}</span>
              </div>

              <!-- Addon details breakdown if active -->
              <div v-if="addonDelivery && deliveryFee > 0" class="flex justify-between text-stone-400">
                <span>Biaya Antar-Jemput</span>
                <span class="font-mono text-white">{{ formatPrice(deliveryFee) }}</span>
              </div>
              <div v-else-if="addonDelivery && deliveryFee === 0" class="flex justify-between text-emerald-400">
                <span>Antar-Jemput (≥3 Hari)</span>
                <span>Gratis</span>
              </div>

              <div v-if="addonHelmet" class="flex justify-between text-stone-400">
                <span>Helm Ekstra (Rp10k x {{ days }} Hari)</span>
                <span class="font-mono text-white">{{ formatPrice(extraHelmetFee) }}</span>
              </div>

              <div v-if="addonPhoneHolder" class="flex justify-between text-stone-400">
                <span>Phone Holder (Rp5k x {{ days }} Hari)</span>
                <span class="font-mono text-white">{{ formatPrice(phoneHolderFee) }}</span>
              </div>
            </div>

            <div class="border-t border-white/10 pt-4 flex justify-between items-end">
              <div>
                <p class="text-xs text-stone-400 font-semibold">Total Pembayaran</p>
                <p class="text-stone-300 text-[10px] mt-0.5">*Bayar saat motor diterima</p>
              </div>
              <p class="font-heading font-black text-2xl text-brand-400 font-mono">{{ formatPrice(grandTotal) }}</p>
            </div>
          </div>

          <!-- Customer info form -->
          <div class="bg-stone-50 rounded-3xl p-6 border border-stone-200/60 shadow-sm flex flex-col space-y-4">
            <h3 class="font-heading font-bold text-base text-stone-900 border-b border-stone-200 pb-2">Informasi Pengantar</h3>

            <!-- Name -->
            <div class="flex flex-col space-y-1">
              <label for="frm-name" class="text-xs font-bold text-stone-700">Nama Lengkap *</label>
              <input
                type="text"
                id="frm-name"
                v-model="name"
                placeholder="Contoh: Budi Santoso"
                class="w-full bg-white border border-stone-300 rounded-xl px-3.5 py-2 text-sm text-stone-900 focus:outline-none focus:border-brand-500 focus:ring-2 focus:ring-brand-200/50"
              />
            </div>

            <!-- Phone -->
            <div class="flex flex-col space-y-1">
              <label for="frm-phone" class="text-xs font-bold text-stone-700">No. WhatsApp *</label>
              <input
                type="tel"
                id="frm-phone"
                v-model="phone"
                placeholder="Contoh: 08123456789"
                class="w-full bg-white border border-stone-300 rounded-xl px-3.5 py-2 text-sm text-stone-900 focus:outline-none focus:border-brand-500 focus:ring-2 focus:ring-brand-200/50"
              />
            </div>

            <!-- Start Date / Time -->
            <div class="grid grid-cols-2 gap-3">
              <div class="flex flex-col space-y-1">
                <label for="frm-date" class="text-xs font-bold text-stone-700">Tanggal Mulai *</label>
                <input
                  type="date"
                  id="frm-date"
                  v-model="startDate"
                  class="w-full bg-white border border-stone-300 rounded-xl px-3 py-2 text-sm text-stone-900 focus:outline-none focus:border-brand-500"
                />
              </div>
              <div class="flex flex-col space-y-1">
                <label for="frm-time" class="text-xs font-bold text-stone-700">Jam Mulai</label>
                <input
                  type="time"
                  id="frm-time"
                  v-model="startTime"
                  class="w-full bg-white border border-stone-300 rounded-xl px-3 py-2 text-sm text-stone-900 focus:outline-none focus:border-brand-500"
                />
              </div>
            </div>

            <!-- Delivery Location -->
            <div v-if="addonDelivery" class="flex flex-col space-y-1">
              <label for="frm-loc" class="text-xs font-bold text-stone-700">Lokasi Antar-Jemput</label>
              <select
                id="frm-loc"
                v-model="deliveryLocation"
                class="w-full bg-white border border-stone-300 rounded-xl px-3.5 py-2 text-sm text-stone-900 font-semibold focus:outline-none focus:border-brand-500"
              >
                <option value="Stasiun Tugu">Stasiun Tugu Jogja</option>
                <option value="Stasiun Lempuyangan">Stasiun Lempuyangan</option>
                <option value="Hotel / Homestay Kota">Hotel / Homestay (Area Kota)</option>
                <option value="Kantor JogjaRide">Ambil Sendiri di Kantor</option>
              </select>
            </div>

            <!-- Notes -->
            <div class="flex flex-col space-y-1">
              <label for="frm-notes" class="text-xs font-bold text-stone-700">Catatan Tambahan (Opsional)</label>
              <textarea
                id="frm-notes"
                v-model="notes"
                placeholder="Contoh: Minta helm ukuran L, taruh jas hujan tambahan."
                rows="2"
                class="w-full bg-white border border-stone-300 rounded-xl px-3.5 py-2 text-sm text-stone-900 focus:outline-none focus:border-brand-500"
              ></textarea>
            </div>

            <!-- Booking Submit CTA -->
            <button
              type="button"
              @click="sendBooking"
              class="book-btn w-full mt-2 inline-flex items-center justify-center py-3.5 rounded-xl font-heading font-black text-sm text-stone-950 bg-brand-400 hover:bg-brand-500 active:scale-95 transition-all duration-200 shadow-md shadow-brand-500/10"
            >
              <svg class="w-4 h-4 fill-current mr-2" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.724-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.725 1.451 5.486.002 9.948-4.463 9.95-9.953.002-2.66-1.033-5.161-2.914-7.045C16.529 1.77 14.032.73 11.37.728 5.885.728 1.424 5.192 1.422 10.683c-.002 1.636.45 3.223 1.309 4.756L1.75 21.024l5.897-1.547-.002-.002z" />
              </svg>
              Pesan via WhatsApp
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
