<script setup>
defineProps({
  product: Object
})
</script>

<template>
  <div class="group cursor-pointer flex flex-col gap-3">
    <div class="relative aspect-[3/4.2] overflow-hidden bg-gray-100">
      <img :src="product.image" class="w-full h-full object-cover transition-opacity duration-500 group-hover:opacity-0 absolute inset-0 z-10" />
      <img :src="product.hoverImage || product.image" class="w-full h-full object-cover absolute inset-0 z-0 scale-105 group-hover:scale-100 transition-transform duration-700" />
      <div v-if="product.tag" class="absolute top-2 left-2 bg-white px-2 py-1 text-[9px] font-bold uppercase tracking-widest z-20">{{ product.tag }}</div>
    </div>
    <div class="flex flex-col space-y-1 mt-2">
      <span class="text-gray-500 text-[10px] uppercase tracking-widest">{{ product.designer }}</span>
      <h3 class="font-normal text-primary text-xs leading-relaxed">{{ product.name }}</h3>
      <div class="text-[10px] text-gray-400" v-if="product.colors">{{ product.colors }} colors</div>
    </div>
  </div>
</template>