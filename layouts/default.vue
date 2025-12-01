<template>
  <div class="min-h-screen flex flex-col font-sans text-primary overflow-x-hidden relative">
    <AppHeader />
    <main class="flex-grow w-full">
      <slot />
    </main>
    
    <AppFooter v-if="$route.path !== '/login'" />
    
    <div class="fixed bottom-4 left-4 z-[90] md:hidden">
       <div class="bg-white border border-gray-200 shadow-xl px-6 py-3 flex items-center gap-4 cursor-pointer">
          <span class="font-bold text-xs uppercase tracking-widest">Get 15% Off</span>
          <button class="w-4 h-4 bg-black text-white rounded-full flex items-center justify-center text-[8px]">×</button>
       </div>
    </div>
  </div>
</template>