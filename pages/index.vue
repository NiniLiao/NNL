<template>
  <div>
    <HeroSection />
    <section class="max-w-[1920px] mx-auto px-4 md:px-8 py-20">
       <div class="mb-12"><h2 class="text-2xl font-serif mb-2">Just In</h2><p class="text-xs text-gray-400">Limited Releases Every Tuesday and Thursday</p></div>
       <div class="grid grid-cols-2 lg:grid-cols-4 gap-x-4 gap-y-12"><ProductCard v-for="p in justInProducts" :key="p.id" :product="p" /></div>
    </section>
    <section class="grid grid-cols-1 md:grid-cols-2">
       <div class="relative h-[80vh] group overflow-hidden"><img src="https://images.unsplash.com/photo-1591047139829-d91aecb6caea?w=1000&q=80" class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" /><div class="absolute bottom-16 left-12 text-white"><h3 class="text-3xl font-serif mb-2 uppercase">Winter Coats</h3><p class="text-xs mb-6 opacity-90">Statement layers that turn cold days into style moments.</p><button class="border border-white px-8 py-3 text-[10px] uppercase tracking-widest hover:bg-white hover:text-black transition-colors">View All</button></div></div>
       <div class="relative h-[80vh] group overflow-hidden"><img src="https://images.unsplash.com/photo-1483985988355-763728e1935b?w=1000&q=80" class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" /><div class="absolute bottom-16 left-12 text-white"><h3 class="text-3xl font-serif mb-2 uppercase">Holiday Gifting</h3><p class="text-xs mb-6 opacity-90">The perfect present, sorted.</p><button class="border border-white px-8 py-3 text-[10px] uppercase tracking-widest hover:bg-white hover:text-black transition-colors">View All</button></div></div>
    </section>
    <section class="max-w-[1920px] mx-auto px-4 md:px-8 py-20">
       <div class="grid grid-cols-2 lg:grid-cols-4 gap-x-4 gap-y-12"><ProductCard v-for="p in moreProducts" :key="p.id" :product="p" /></div>
    </section>
  </div>
</template>
<script setup>
import { ref } from 'vue'
const justInProducts = ref([{ id: 1, name: 'Rosie Lapel Tweed Cinched Dress', designer: 'Paulus Erasmus', image: 'https://images.unsplash.com/photo-1595777457583-95e059d581b8?w=800&q=80' }, { id: 2, name: 'Star Straight Leg Jeans', designer: 'Angelo Lapiccirella', image: 'https://images.unsplash.com/photo-1541099649105-f69ad21f3246?w=800&q=80', colors: '4' }, { id: 3, name: 'Monroe Silver Back Pocket Jeans', designer: 'Anna Pang', image: 'https://images.unsplash.com/photo-1584370848010-d7cc637703ef?w=800&q=80', colors: '2' }, { id: 4, name: 'Eleanor Ombre Sleeveless Vest', designer: 'Elvira Gasanova', image: 'https://images.unsplash.com/photo-1516762689617-e1cffcef479d?w=800&q=80' }])
const moreProducts = ref([{ id: 5, name: 'Oiled Leather Shoulder Bag', designer: 'Sophie Jousse', image: 'https://images.unsplash.com/photo-1590874103328-eac38a683ce7?w=800&q=80', tag: 'New' }, { id: 6, name: 'Cropped Tweed Jacket', designer: 'Alex Rotin', image: 'https://images.unsplash.com/photo-1548624149-f321f654b681?w=800&q=80' }, { id: 7, name: 'Cashmere Scarf', designer: 'Soft Touch', image: 'https://images.unsplash.com/photo-1520903920243-00d872a2d1c9?w=800&q=80' }, { id: 8, name: 'Structured Handbag', designer: 'Sophie Jousse', image: 'https://images.unsplash.com/photo-1584917865442-de89df76afd3?w=800&q=80' }])
</script>