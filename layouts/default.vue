<script setup>
import { useRoute } from 'vue-router'
import AppHeader from '~/components/AppHeader.vue'
import AppFooter from '~/components/AppFooter.vue'

const route = useRoute()
</script>

<template>
  <div class="min-h-screen flex flex-col font-sans text-primary overflow-x-hidden relative">
    <AppHeader />
    <main class="flex-grow w-full">
      <slot />
    </main>
    
    <AppFooter v-if="route?.path && !['/account/login', '/account/register'].includes(route.path)" />
    
    <div class="fixed bottom-4 left-4 z-[90] md:hidden" v-if="!['/account/login', '/account/register'].includes(route.path)">
       <div class="bg-white border border-gray-200 shadow-xl px-6 py-3 flex items-center gap-4 cursor-pointer">
          <span class="font-bold text-xs uppercase tracking-widest">Get 15% Off</span>
          <button class="w-4 h-4 bg-black text-white rounded-full flex items-center justify-center text-[8px]">×</button>
       </div>
    </div>

    <div v-if="route.path && route.path.startsWith('/account')" class="fixed bottom-8 right-8 z-[90]">
        <button class="bg-[#E88F77] text-white px-6 py-3 rounded-full shadow-lg flex items-center gap-2 font-bold text-sm hover:opacity-90 transition-opacity">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v13m0-13V6a2 2 0 112 2h-2zm0 0V5.5A2.5 2.5 0 109.5 8H12zm-7 4h14M5 12a2 2 0 110-4h14a2 2 0 110 4M5 12v7a2 2 0 002 2h10a2 2 0 002-2v-7"></path></svg>
            Rewards
        </button>
    </div>
  </div>
</template>
<style scoped></style>