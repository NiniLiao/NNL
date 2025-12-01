<template>
  <div class="fixed inset-0 z-[100] flex items-center justify-center px-4">
    <div class="absolute inset-0 bg-black/40 backdrop-blur-sm transition-opacity" @click="$emit('close')"></div>
    <div class="bg-white w-full max-w-lg relative z-10 p-8 shadow-2xl animate-fade-in max-h-[90vh] overflow-y-auto">
       <div class="flex justify-between items-start mb-8"><h2 class="font-serif text-xl tracking-wide">Ship To</h2><button @click="$emit('close')" class="text-gray-400 hover:text-black transition-colors"><svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg></button></div>
       <div class="mb-6"><p class="text-xs text-gray-500 mb-4">Currently Ship To</p><div class="flex justify-between items-center text-sm font-medium bg-gray-50 p-3 rounded"><div class="flex items-center gap-3"><img src="https://flagcdn.com/w40/tw.png" class="w-6 h-auto shadow-sm rounded-sm" /><span>Taiwan Region</span></div><span>TWD $</span></div></div>
       <div class="border-b border-dashed border-gray-200 mb-6"></div>
       <div class="mb-6"><p class="text-xs text-gray-500 mb-4">Country</p><ul class="space-y-5"><li class="flex justify-between items-center text-sm group cursor-pointer hover:opacity-70" v-for="c in countries" :key="c.name"><div class="flex items-start gap-3"><img :src="c.flag" class="w-6 h-auto mt-0.5 shadow-sm rounded-sm" /><div class="flex flex-col"><span class="font-medium">{{ c.name }}</span><span v-if="c.sub" class="text-[10px] text-gray-400 mt-0.5">{{ c.sub }}</span></div></div><span class="text-gray-500">{{ c.currency }}</span></li></ul></div>
       <div class="border-b border-dashed border-gray-200 mb-6"></div>
       <div><p class="text-xs text-gray-500 mb-4">Region</p><ul class="space-y-5"><li class="flex justify-between items-center text-sm group cursor-pointer hover:opacity-70" v-for="r in regions" :key="r.name"><div class="flex items-center gap-3"><img :src="r.flag" class="w-6 h-auto shadow-sm rounded-sm" /><span class="font-medium">{{ r.name }}</span></div><span class="text-gray-500">{{ r.currency }}</span></li></ul></div>
    </div>
  </div>
</template>
<script setup>
const countries = [{ name: 'Canada', sub: '(Ontario, British Columbia, Quebec and Alberta)', currency: 'CAD $', flag: 'https://flagcdn.com/w40/ca.png' }, { name: 'Singapore', currency: 'SGD $', flag: 'https://flagcdn.com/w40/sg.png' }, { name: 'United Kingdom', currency: 'GBP £', flag: 'https://flagcdn.com/w40/gb.png' }, { name: 'United States', currency: 'USD $', flag: 'https://flagcdn.com/w40/us.png' }]
const regions = [{ name: 'Hong Kong SAR', currency: 'HKD $', flag: 'https://flagcdn.com/w40/hk.png' }, { name: 'Macao SAR', currency: 'MOP P', flag: 'https://flagcdn.com/w40/mo.png' }, { name: 'Taiwan Region', currency: 'TWD $', flag: 'https://flagcdn.com/w40/tw.png' }]
</script>
<style scoped>.animate-fade-in { animation: fadeIn 0.3s ease-out; } @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }</style>