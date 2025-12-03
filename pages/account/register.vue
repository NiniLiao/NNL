<script setup>
import { ref } from 'vue'
import AppFooter from '~/components/AppFooter.vue'
const showPassword = ref(false)
const perksChecked = ref(false)
</script>

<template>
  <div class="w-full relative bg-white">
    <div class="relative w-full min-h-screen bg-black flex items-center justify-center">
        <img src="https://images.unsplash.com/photo-1534959309653-4632b79e782b?w=2000&q=80" class="absolute inset-0 w-full h-full object-cover opacity-60" />
        <div class="absolute inset-0 bg-black/40"></div>
        
        <div class="relative z-10 w-full max-w-sm px-4 py-32 md:py-40">
           <h1 class="text-white text-2xl font-medium mb-6 text-left">Register</h1>
              
           <form class="space-y-5 text-left">
              <input type="text" placeholder="First name" class="w-full bg-transparent border-b border-white/30 text-white placeholder-gray-400 py-3 outline-none focus:border-white transition-colors text-sm" />
              <input type="text" placeholder="Last name" class="w-full bg-transparent border-b border-white/30 text-white placeholder-gray-400 py-3 outline-none focus:border-white transition-colors text-sm" />
              <input type="email" placeholder="Email address" class="w-full bg-transparent border-b border-white/30 text-white placeholder-gray-400 py-3 outline-none focus:border-white transition-colors text-sm" />
              
              <div class="relative">
                 <input :type="showPassword ? 'text' : 'password'" placeholder="Create Password" class="w-full bg-transparent border-b border-white/30 text-white placeholder-gray-400 py-3 outline-none focus:border-white transition-colors text-sm" />
                 <button type="button" class="absolute right-0 top-3 text-gray-400 hover:text-white" @click="showPassword = !showPassword">
                     <svg v-if="showPassword" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"></path></svg>
                     <svg v-else class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M13.875 18.825A10.05 10.05 0 0112 19c-4.478 0-8.268-2.943-9.543-7a9.97 9.97 0 011.563-3.029m5.858.908a3 3 0 114.243 4.243M9.878 9.878l4.242 4.242M9.88 9.88l-3.29-3.29m7.532 7.532l3.29 3.29M3 3l3.59 3.59m0 0A9.953 9.953 0 0112 5c4.478 0 8.268 2.943 9.543 7a10.025 10.025 0 01-4.132 5.411m0 0L21 21"></path></svg>
                 </button>
              </div>

              <p class="text-[10px] text-left text-gray-400 mt-1 leading-relaxed">
                 By registering, your account will be subject to the <a href="#" class="underline text-gray-300 hover:text-white">Terms and Conditions</a> & <a href="#" class="underline text-gray-300 hover:text-white">Privacy Policy</a>.
              </p>

              <button type="submit" class="w-full bg-white text-black py-3 text-sm font-bold uppercase tracking-widest hover:bg-gray-200 transition-colors mt-4">Create Account</button>
           </form>
           
           <div class="flex items-start gap-3 mt-6 text-left group cursor-pointer" @click="perksChecked = !perksChecked">
               <div class="w-4 h-4 border border-white/50 flex-shrink-0 rounded-full flex items-center justify-center mt-0.5 transition-colors" :class="{'bg-white border-white': perksChecked}">
                   <svg v-if="perksChecked" class="w-3 h-3 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7"></path></svg>
               </div>
               <p class="text-[10px] text-gray-400 leading-snug select-none">Sign up for exclusive perks with NNL Rewards, and enjoy 15% off your first order. What Will I Receive?</p>
           </div>

           <div class="my-8 text-xs font-bold text-white text-left">Already have an account?</div>
           
           <NuxtLink to="/account/login" class="block w-full border border-white text-white py-3 text-sm font-medium hover:bg-white hover:text-black transition-colors mb-8 uppercase tracking-widest text-center">Sign in</NuxtLink>
           
           <div class="flex items-center gap-4 mb-8"><div class="h-[1px] bg-white/30 flex-grow"></div><span class="text-xs text-white/50 uppercase tracking-widest">OR</span><div class="h-[1px] bg-white/30 flex-grow"></div></div>
           
           <div class="flex justify-center gap-4 pb-10">
              <button class="w-10 h-10 bg-white rounded-full flex items-center justify-center hover:opacity-90 transform hover:scale-105 transition-transform"><img src="https://www.svgrepo.com/show/475656/google-color.svg" class="w-5 h-5" /></button>
              <button class="w-10 h-10 bg-[#1877F2] rounded-full flex items-center justify-center hover:opacity-90 transform hover:scale-105 transition-transform"><svg class="w-5 h-5 text-white" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.791-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg></button>
           </div>
        </div>
    </div>
    
    <div class="bg-white py-24 px-6 border-b border-gray-100">
       <div class="max-w-[1920px] mx-auto grid grid-cols-1 md:grid-cols-3 gap-16 text-center">
          <div><div class="flex justify-center mb-6"><svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="1" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg></div><h4 class="text-xs font-bold uppercase tracking-widest mb-3 text-black">Exclusive Collections from Global Designers</h4><p class="text-[10px] text-gray-500 leading-relaxed max-w-xs mx-auto">Collaborating with over 350 esteemed fashion designers worldwide, NNL offers an exclusive collection of designer styles, available only on our platform.</p></div>
          <div><div class="flex justify-center mb-6"><svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="1" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"></path></svg></div><h4 class="text-xs font-bold uppercase tracking-widest mb-3 text-black">Free Shipping</h4><p class="text-[10px] text-gray-500 leading-relaxed max-w-xs mx-auto">Free shipping makes your shopping experience at NNL even better.</p></div>
          <div><div class="flex justify-center mb-6"><svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="1" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"></path></svg></div><h4 class="text-xs font-bold uppercase tracking-widest mb-3 text-black">Loyalty Rewards</h4><p class="text-[10px] text-gray-500 leading-relaxed max-w-xs mx-auto">Join NNL Rewards and enjoy points, perks, and private designer access.</p></div>
       </div>
    </div>
    
    <AppFooter :show-media="false" :show-badges="false" />
  </div>
</template>