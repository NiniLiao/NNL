<template>
  <div>
    <header class="absolute top-0 left-0 w-full z-40 transition-colors duration-200 border-b border-transparent" :class="[(isHovered || activeMenu || isMobileMenuOpen || isSearchOpen || isSolidHeader) ? 'bg-white text-black border-gray-100 shadow-sm' : 'bg-transparent text-white hover:bg-white hover:text-black']" @mouseenter="isHovered = true" @mouseleave="handleMouseLeave">
      <div class="w-full text-center py-2 px-2 border-b border-current border-opacity-10 transition-opacity duration-300 bg-[#0B1215] text-white">
        <p class="text-[9px] md:text-[10px] uppercase tracking-[0.15em] md:tracking-[0.2em] font-medium truncate">BLACK FRIDAY UP TO 60% OFF | <span class="font-bold">BIGGEST EVENT OF THE YEAR</span></p>
      </div>
      <div class="flex items-center justify-between px-4 md:px-8 h-14 md:h-16 w-full max-w-[1920px] mx-auto relative">
        <transition name="fade" mode="out-in">
            <div v-if="isSearchOpen" class="w-full h-full flex items-center justify-center animate-fade-in">
                <div class="w-full max-w-5xl relative flex items-center">
                    <div class="w-full bg-gray-100 flex items-center px-4 py-2 md:py-3 rounded-sm">
                        <svg class="w-5 h-5 text-gray-500 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                        <input ref="searchInput" type="text" placeholder="Search products..." class="bg-transparent w-full outline-none text-sm text-black placeholder-gray-400" />
                        <button @click="isSearchOpen = false" class="ml-2 hover:text-gray-700"><svg class="w-5 h-5 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg></button>
                    </div>
                </div>
            </div>
            <div v-else class="w-full flex items-center justify-between h-full">
                <button class="xl:hidden p-2 -ml-2 hover:opacity-70" @click="isMobileMenuOpen = true"><svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 6h16M4 12h16M4 18h16"></path></svg></button>
                <div class="absolute left-1/2 -translate-x-1/2 xl:static xl:translate-x-0 xl:mr-12"><NuxtLink to="/" class="text-xl md:text-2xl font-bold tracking-tight">NNL</NuxtLink></div>
                <nav class="hidden xl:flex items-center gap-5 text-[10px] 2xl:text-[11px] font-bold tracking-widest uppercase flex-grow h-full justify-center lg:justify-start">
                  <div v-for="item in menuItems" :key="item.key" class="h-full flex items-center relative group cursor-pointer" @mouseenter="activeMenu = item.key"><NuxtLink :to="item.link" class="transition-colors py-6 border-b-2 border-transparent hover:border-black whitespace-nowrap" :class="{'text-accent': item.key === 'sale', 'border-black': activeMenu === item.key && (isHovered || activeMenu)}">{{ item.name }}</NuxtLink></div>
                </nav>
                <div class="flex items-center gap-2 md:gap-5 text-xs font-medium tracking-wide">
                  <button class="hidden lg:flex items-center gap-2 hover:opacity-70" @click="isModalOpen = true"><span class="hidden xl:inline">Taiwan Region | TWD $</span><span class="xl:hidden">TWD $</span></button>
                  <button class="hover:opacity-70" @click="toggleSearch"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg></button>
                  
                  <NuxtLink to="/account/login" class="hover:opacity-70"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path></svg></NuxtLink>
                  
                  <NuxtLink to="/wishlist" class="hover:opacity-70"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"></path></svg></NuxtLink>
                  <button class="hover:opacity-70 relative"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg><span class="absolute -top-1 -right-1 w-2 h-2 bg-accent rounded-full border border-white text-[8px] flex items-center justify-center text-white font-bold">1</span></button>
                </div>
            </div>
        </transition>
      </div>
      <transition enter-active-class="transition duration-200 ease-out" enter-from-class="opacity-0 -translate-y-2" enter-to-class="opacity-100 translate-y-0" leave-active-class="transition duration-150 ease-in" leave-from-class="opacity-100 translate-y-0" leave-to-class="opacity-0 -translate-y-2">
        <div v-if="activeContent && !isMobileMenuOpen && !isSearchOpen" class="hidden xl:block absolute top-full left-0 w-full bg-white text-primary border-t border-gray-100 shadow-xl py-12 px-12 max-h-[80vh] overflow-y-auto" @mouseenter="isHovered = true" @mouseleave="activeMenu = null">
          <div class="max-w-[1920px] mx-auto grid gap-8" :class="activeMenu === 'bags' ? 'grid-cols-4' : 'grid-cols-5'">
             <div class="flex flex-col space-y-4"><h4 class="text-xs font-bold uppercase tracking-widest mb-2">{{ activeContent.col1.title }}</h4><ul class="space-y-3 text-xs text-gray-500 font-medium"><li v-for="link in activeContent.col1.links" :key="link">{{ link }}</li></ul></div>
             <div class="flex flex-col space-y-4"><h4 class="text-xs font-bold uppercase tracking-widest mb-2">{{ activeContent.col2.title }}</h4><ul class="space-y-3 text-xs text-gray-500 font-medium"><li v-for="link in activeContent.col2.links" :key="link">{{ link }}</li></ul></div>
             <div class="group cursor-pointer" v-if="activeContent.image1"><div class="aspect-[3/4] overflow-hidden bg-gray-100 mb-3"><img :src="activeContent.image1.src" class="w-full h-full object-cover" /></div><p class="text-xs text-gray-500">{{ activeContent.image1.text }}</p></div>
             <div class="group cursor-pointer" v-if="activeContent.image2"><div class="aspect-[3/4] overflow-hidden bg-gray-100 mb-3"><img :src="activeContent.image2.src" class="w-full h-full object-cover" /></div><p class="text-xs text-gray-500">{{ activeContent.image2.text }}</p></div>
             <div class="group cursor-pointer" v-if="activeContent.promo"><div class="aspect-[3/4] bg-black text-white flex flex-col justify-center items-center text-center p-6 relative"><p class="text-promo text-5xl italic">{{ activeContent.promo.discount }}%</p><p class="text-xs mt-4">{{ activeContent.promo.desc }}</p></div></div>
          </div>
        </div>
      </transition>
    </header>

    <transition enter-active-class="transition duration-300 ease-out" enter-from-class="-translate-x-full" enter-to-class="translate-x-0" leave-active-class="transition duration-300 ease-in" leave-from-class="translate-x-0" leave-to-class="-translate-x-full">
        <div v-if="isMobileMenuOpen" class="fixed inset-y-0 left-0 w-full max-w-md bg-white z-[100] flex flex-col xl:hidden overflow-hidden text-primary">
            <div class="w-full text-center py-2 px-2 bg-[#0B1215] text-white"><p class="text-[9px] uppercase tracking-[0.15em] font-medium">BLACK FRIDAY UP TO 60% OFF | BIGGEST EVENT...</p></div>
            <div v-if="!mobileSubMenu" class="flex flex-col h-full">
                <div class="flex items-center justify-between px-4 h-16 border-b border-gray-100 flex-shrink-0">
                     <button @click="isMobileMenuOpen = false" class="p-2 -ml-2"><svg class="w-6 h-6 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg></button>
                     <NuxtLink to="/" @click="isMobileMenuOpen = false" class="text-2xl font-bold font-serif tracking-tight">NNL</NuxtLink>
                     <div class="flex items-center gap-2">
                        <button @click="isMobileMenuOpen = false; toggleSearch()"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg></button>
                        
                        <NuxtLink to="/account/login" @click="isMobileMenuOpen = false"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path></svg></NuxtLink>
                        
                        <NuxtLink to="/wishlist" @click="isMobileMenuOpen = false"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"></path></svg></NuxtLink>
                        <div class="relative"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg><span class="absolute -top-1 -right-1 w-2 h-2 bg-accent rounded-full border border-white text-[8px] flex items-center justify-center text-white font-bold">1</span></div>
                     </div>
                </div>
                <div class="overflow-y-auto flex-grow p-6">
                    <nav class="flex flex-col space-y-6">
                        <div v-for="item in menuItems" :key="item.key" class="flex justify-between items-center cursor-pointer border-b border-gray-50 pb-3" @click="handleMobileClick(item)">
                            <span class="text-sm font-bold uppercase tracking-widest" :class="{'text-accent': item.key === 'sale'}">{{ item.name }}</span>
                            <span v-if="menuData[item.key]" class="text-gray-400"><svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 5l7 7-7 7"></path></svg></span>
                        </div>
                    </nav>
                    <div class="mt-8 border-t border-gray-50 pt-6">
                        <NuxtLink to="/account/login" @click="isMobileMenuOpen = false" class="text-sm font-bold uppercase tracking-widest">Sign In</NuxtLink>
                    </div>
                </div>
                <div class="p-5 border-t border-gray-100 mt-auto bg-white cursor-pointer hover:bg-gray-50 flex-shrink-0" @click="isModalOpen = true">
                    <div class="flex items-center justify-between">
                       <div class="flex items-center gap-2"><span class="text-[10px] font-bold uppercase tracking-widest text-gray-400">SHIP TO</span><img src="https://flagcdn.com/w40/tw.png" class="w-5 h-auto shadow-sm" /><span class="text-[10px] font-bold uppercase tracking-widest">Taiwan Region | TWD $</span></div>
                       <svg class="w-4 h-4 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 5l7 7-7 7"></path></svg>
                    </div>
                </div>
            </div>

            <div v-else class="flex flex-col h-full bg-white text-primary overflow-hidden">
                <div class="flex items-center justify-between px-4 h-16 border-b border-gray-100 flex-shrink-0">
                     <button @click="isMobileMenuOpen = false" class="p-2 -ml-2"><svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg></button>
                     <NuxtLink to="/" @click="isMobileMenuOpen = false; mobileSubMenu = null" class="text-2xl font-bold font-serif tracking-tight">NNL</NuxtLink>
                     <div class="flex items-center gap-2"><button @click="isMobileMenuOpen = false; toggleSearch()"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg></button>
                     <NuxtLink to="/account/login" @click="isMobileMenuOpen = false"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path></svg></NuxtLink>
                     <NuxtLink to="/wishlist" @click="isMobileMenuOpen = false"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"></path></svg></NuxtLink><div class="relative"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg><span class="absolute -top-1 -right-1 w-2 h-2 bg-accent rounded-full border border-white text-[8px] flex items-center justify-center text-white font-bold">1</span></div></div>
                </div>
                <div class="flex items-center px-6 py-4 border-b border-gray-100 gap-2 cursor-pointer hover:bg-gray-50 flex-shrink-0" @click="mobileSubMenu = null"><svg class="w-4 h-4 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg><span class="text-xs font-bold uppercase tracking-widest">{{ mobileSubMenu }}</span></div>
                <div class="overflow-y-auto flex-grow p-6">
                     <div class="mb-8" v-if="activeContent">
                        <div class="mb-6 border-b border-gray-100 pb-4"><h4 class="text-xs font-bold uppercase tracking-widest mb-3 flex justify-between items-center cursor-pointer" @click="toggleAccordion('col1')">{{ activeContent.col1.title }} <span class="text-gray-400 transform transition-transform" :class="{'rotate-180': accordions.col1}">↓</span></h4><ul v-if="accordions.col1" class="space-y-4 text-xs text-gray-500 font-medium pl-1 mt-2"><li v-for="link in activeContent.col1.links" :key="link" class="hover:text-black">{{ link }}</li></ul></div>
                        <div class="mb-8 border-b border-gray-100 pb-4"><h4 class="text-xs font-bold uppercase tracking-widest mb-3 flex justify-between items-center cursor-pointer" @click="toggleAccordion('col2')">{{ activeContent.col2.title }} <span class="text-gray-400 transform transition-transform" :class="{'rotate-180': accordions.col2}">↓</span></h4><ul v-if="accordions.col2" class="space-y-4 text-xs text-gray-500 font-medium pl-1 mt-2"><li v-for="link in activeContent.col2.links" :key="link" class="hover:text-black">{{ link }}</li></ul></div>
                        <div class="grid grid-cols-2 gap-3 mb-4"><div v-if="activeContent.image1"><img :src="activeContent.image1.src" class="w-full aspect-[3/4] object-cover" /><p class="text-[10px] mt-2 text-gray-500">{{ activeContent.image1.text }}</p></div><div v-if="activeContent.image2"><img :src="activeContent.image2.src" class="w-full aspect-[3/4] object-cover" /><p class="text-[10px] mt-2 text-gray-500">{{ activeContent.image2.text }}</p></div></div>
                        <div v-if="activeContent.promo" class="bg-black text-white p-8 text-center relative overflow-hidden mt-6"><div class="absolute top-0 left-1/2 -translate-x-1/2 w-[1px] h-8 bg-gray-700"></div><p class="text-xs uppercase tracking-widest mb-1 text-gray-400 mt-4">Up To</p><p class="text-promo text-5xl font-serif italic mb-2">{{ activeContent.promo.discount }}%</p><p class="text-xs uppercase tracking-widest text-gray-400 mb-4">Off</p><p class="text-[10px] text-gray-400 max-w-[200px] mx-auto leading-relaxed">{{ activeContent.promo.desc }}</p></div>
                     </div>
                </div>
                <div class="p-5 border-t border-gray-100 mt-auto bg-white cursor-pointer hover:bg-gray-50 flex-shrink-0" @click="isModalOpen = true">
                    <div class="flex items-center justify-between">
                       <div class="flex items-center gap-2"><span class="text-[10px] font-bold uppercase tracking-widest text-gray-400">SHIP TO</span><img src="https://flagcdn.com/w40/tw.png" class="w-5 h-auto shadow-sm" /><span class="text-[10px] font-bold uppercase tracking-widest">Taiwan Region | TWD $</span></div>
                       <svg class="w-4 h-4 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 5l7 7-7 7"></path></svg>
                    </div>
                </div>
            </div>
        </div>
    </transition>
    <RegionModal v-if="isModalOpen" @close="isModalOpen = false" />
    <div v-if="isMobileMenuOpen" class="fixed inset-0 bg-black/50 z-[55] xl:hidden backdrop-blur-sm" @click="isMobileMenuOpen = false"></div>
  </div>
</template>
<script setup>
import { ref, computed, reactive, nextTick } from 'vue'
import { useRouter, useRoute } from 'vue-router'
const route = useRoute()
const router = useRouter()
const isHovered = ref(false)
const activeMenu = ref(null)
const isMobileMenuOpen = ref(false)
const isModalOpen = ref(false)
const isSearchOpen = ref(false)
const searchInput = ref(null)
const mobileSubMenu = ref(null)
const accordions = reactive({ col1: true, col2: false })
const isSolidHeader = computed(() => route.path === '/wishlist')
const handleMouseLeave = () => { isHovered.value = false; activeMenu.value = null }
const toggleSearch = () => { isSearchOpen.value = !isSearchOpen.value; if(isSearchOpen.value) nextTick(() => searchInput.value?.focus()) }
const handleMobileClick = (item) => { if (menuData[item.key]) { mobileSubMenu.value = item.key; accordions.col1 = true; accordions.col2 = false } else { isMobileMenuOpen.value = false; router.push(item.link) } }
const toggleAccordion = (col) => { accordions[col] = !accordions[col] }
const menuItems = [ { name: 'Black Friday Sale', key: 'sale', link: '/sale' }, { name: 'New', key: 'new', link: '/new' }, { name: 'Best Sellers', key: 'best-sellers', link: '/best-sellers' }, { name: 'Designers', key: 'designers', link: '/designers' }, { name: 'Bags', key: 'bags', link: '/bags' }, { name: 'Clothing', key: 'clothing', link: '/clothing' }, { name: 'Denim', key: 'denim', link: '/denim' }, { name: 'Editorial', key: 'editorial', link: '/editorial' }, { name: 'About', key: 'about', link: '/about' } ]
const menuData = { bags: { col1: { title: 'Size', links: ['Small Bags', 'Medium Bags', 'Large Bags', 'View All'] }, col2: { title: 'Category', links: ['Bucket Bags', 'Shoulder Bags', 'Tote Bags', 'Accessories', 'View All'] }, image1: { src: 'https://images.unsplash.com/photo-1590874103328-eac38a683ce7?w=500&q=80', text: 'Suede Edit' }, image2: null, promo: { discount: '15', desc: 'Only bag discount of the season.', footer: 'Shop Black Friday' } }, denim: { col1: { title: 'All Jeans', links: ['Wide-Leg Jeans', 'Straight Jeans', 'Barrel Jeans', 'Relaxed Jeans', 'Flare & Bootcut & Skinny'] }, col2: { title: 'All Denim', links: ['Denim Dresses & Skirts', 'Denim Jackets', 'Denim Shirts', 'Denim Shorts'] }, image1: { src: 'https://images.unsplash.com/photo-1541099649105-f69ad21f3246?w=500&q=80', text: 'All Denim' }, image2: { src: 'https://images.unsplash.com/photo-1584370848010-d7cc637703ef?w=500&q=80', text: 'New Denim' }, promo: { discount: '60', desc: 'Designer denim at our best prices this year.', footer: 'Shop Black Friday' } }, clothing: { col1: { title: 'All Clothing', links: ['Jackets & Blazers', 'Denim', 'Dresses', 'Coats & Puffer', 'Pants', 'Sweaters'] }, col2: { title: 'Featured', links: ['Short Coats', 'Burgundy & Oxblood', 'Suede & Corduroys', 'New Looks', 'Fall Essentials'] }, image1: { src: 'https://images.unsplash.com/photo-1542272201-b1ca555f8505?w=500&q=80', text: 'Coats' }, image2: { src: 'https://images.unsplash.com/photo-1551488852-7a304fa73846?w=500&q=80', text: 'Jackets' }, promo: { discount: '60', desc: "The event you don't want to miss.", footer: 'Shop Black Friday' } } }
const activeContent = computed(() => { const key = mobileSubMenu.value || activeMenu.value; return menuData[key] || null })
</script>