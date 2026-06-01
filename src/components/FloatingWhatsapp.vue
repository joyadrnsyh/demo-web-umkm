<script setup>
const whatsappNumber = '6281228229221'
const defaultMessage = 'Halo JogjaRide! Saya ingin bertanya seputar sewa motor di Jogja.'
const waUrl = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(defaultMessage)}`
</script>

<template>
  <a
    :href="waUrl"
    target="_blank"
    class="fixed bottom-6 right-6 z-50 flex items-center justify-center w-14 h-14 bg-emerald-500 text-white rounded-full shadow-lg hover:bg-emerald-600 hover:scale-105 active:scale-95 transition-all duration-300 group"
    aria-label="Tanya via WhatsApp"
  >
    <!-- Pulse Effect -->
    <span class="absolute inset-0 rounded-full bg-emerald-500 opacity-25 animate-ping group-hover:hidden"></span>
    
    <!-- SVG WhatsApp Icon -->
    <svg class="w-7 h-7 relative z-10" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
      <path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.724-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.725 1.451 5.486.002 9.948-4.463 9.95-9.953.002-2.66-1.033-5.161-2.914-7.045C16.529 1.77 14.032.73 11.37.728 5.885.728 1.424 5.192 1.422 10.683c-.002 1.636.45 3.223 1.309 4.756L1.75 21.024l5.897-1.547-.002-.002zM17.82 14.87c-.334-.167-1.974-.975-2.28-1.087-.306-.113-.53-.167-.75.167-.22.335-.855 1.087-1.048 1.31-.193.224-.387.25-.72.083-.334-.167-1.41-.52-2.685-1.657-1.002-.894-1.678-2.001-1.873-2.336-.196-.334-.02-.515.147-.68.15-.148.334-.39.502-.585.167-.195.222-.334.334-.557.112-.223.056-.417-.028-.585-.084-.167-.75-1.812-1.027-2.482-.27-.65-.54-.56-.75-.572-.193-.01-.416-.012-.64-.012-.224 0-.588.084-.895.42-.307.334-1.173 1.147-1.173 2.793 0 1.646 1.198 3.236 1.365 3.46.168.223 2.358 3.599 5.712 5.047.798.344 1.42.55 1.905.704.802.256 1.533.22 2.11.134.64-.096 1.975-.808 2.252-1.59.278-.782.278-1.45.194-1.59-.083-.14-.306-.223-.64-.39z" />
    </svg>
  </a>
</template>
