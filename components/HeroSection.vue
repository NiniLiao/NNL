<template>
  <div class="relative w-full h-[100dvh] flex items-center justify-center overflow-hidden bg-black">
    <img src="https://images.unsplash.com/photo-1576566588028-4147f3842f27?q=80&w=2070&auto=format&fit=crop" class="absolute inset-0 w-full h-full object-cover opacity-90" />
    <div class="absolute inset-0 bg-black/20"></div>
    <div class="relative z-10 text-center text-white px-4 flex flex-col items-center">
      <h1 class="text-4xl md:text-6xl lg:text-7xl font-sans font-bold tracking-tight mb-2 drop-shadow-md">BLACK FRIDAY</h1>
      <div class="text-6xl md:text-8xl lg:text-9xl font-light mb-4 flex items-baseline gap-2">
         <span class="text-2xl md:text-4xl uppercase tracking-widest font-bold translate-y-[-20px]">Up To</span>
         <span>60</span>
         <span class="text-3xl md:text-5xl">%</span>
         <span class="text-2xl md:text-4xl uppercase tracking-widest font-bold translate-y-[-20px]">Off</span>
      </div>
      <p class="text-sm md:text-base font-light tracking-wide mb-12">Biggest Sale of the Year. Free Gifts with Purchase.</p>
      <button class="border-b border-white pb-1 text-sm uppercase tracking-[0.2em] hover:text-gray-300 hover:border-gray-300 transition-colors">Shop Sale</button>
    </div>
  </div>
</template>