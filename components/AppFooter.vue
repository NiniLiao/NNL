<template>
  <footer class="bg-white border-t border-gray-100">
    <div v-if="showMedia" class="pt-20 pb-12 px-6 border-b border-gray-100 text-center">
       <h3 class="text-xl font-serif mb-8">In The Media</h3>
       <p class="text-xs text-gray-500 max-w-2xl mx-auto mb-10 leading-relaxed">NNL has been recognized for its distinctive dialogue within the fashion world. These features celebrate our commitment to the stories behind each piece—bringing design narratives to the forefront.</p>
       <div class="flex justify-center items-center gap-6 md:gap-12 grayscale opacity-60 flex-wrap"><span class="font-serif font-bold text-xl">WWD</span><span class="font-serif font-bold text-xl">VOGUE</span><span class="font-serif font-bold text-xl">FASHIONISTA</span><span class="font-serif font-bold text-xl">TZR</span></div>
    </div>
    <div v-if="showBadges" class="py-16 px-6 border-b border-gray-100">
       <div class="max-w-[1920px] mx-auto grid grid-cols-1 md:grid-cols-3 gap-12 text-center">
          <div><div class="flex justify-center mb-6"><svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="1" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg></div><h4 class="text-xs font-bold uppercase tracking-widest mb-3 text-black">Exclusive Collections</h4><p class="text-[10px] text-gray-500 leading-relaxed max-w-xs mx-auto">Collaborating with over 350 esteemed fashion designers worldwide, NNL offers an exclusive collection of designer styles, available only on our platform.</p></div>
          <div><div class="flex justify-center mb-6"><svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="1" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"></path></svg></div><h4 class="text-xs font-bold uppercase tracking-widest mb-3 text-black">Free Shipping</h4><p class="text-[10px] text-gray-500 leading-relaxed max-w-xs mx-auto">Free shipping makes your shopping experience at NNL even better.</p></div>
          <div><div class="flex justify-center mb-6"><svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="1" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"></path></svg></div><h4 class="text-xs font-bold uppercase tracking-widest mb-3 text-black">Loyalty Rewards</h4><p class="text-[10px] text-gray-500 leading-relaxed max-w-xs mx-auto">Join NNL Rewards and enjoy points, perks, and private designer access.</p></div>
       </div>
    </div>
    <div class="pt-16 pb-12 px-6">
        <div class="max-w-[1920px] mx-auto grid grid-cols-1 lg:grid-cols-4 gap-12">
            <div class="lg:col-span-2">
                <h4 class="font-bold text-sm mb-4">Enjoy 15% off your first order</h4>
                <p class="text-xs text-gray-500 mb-6 max-w-sm">Subscribe to our emails and claim your exclusive discount code (terms and conditions apply).</p>
                <div class="flex border-b border-black pb-2 max-w-md">
                    <input type="email" placeholder="Email address" class="flex-grow outline-none text-sm bg-transparent" />
                    <button class="text-xs font-bold uppercase tracking-widest">Subscribe</button>
                </div>
                <div class="mt-8"><p class="text-[10px] text-gray-400 mb-3 uppercase tracking-widest">Follow us</p><div class="flex gap-4 text-black"><div class="w-5 h-5 bg-black rounded-full text-white flex items-center justify-center text-[10px]">f</div><div class="w-5 h-5 bg-black rounded-full text-white flex items-center justify-center text-[10px]">in</div><div class="w-5 h-5 bg-black rounded-full text-white flex items-center justify-center text-[10px]">p</div><div class="w-5 h-5 bg-black rounded-full text-white flex items-center justify-center text-[10px]">y</div><div class="w-5 h-5 bg-black rounded-full text-white flex items-center justify-center text-[10px]">t</div></div></div>
                <div class="mt-8"><p class="text-[10px] text-gray-400 mb-3 uppercase tracking-widest">NNL accepts</p><div class="flex gap-2 opacity-80 flex-wrap"><img src="https://upload.wikimedia.org/wikipedia/commons/5/5e/Visa_Inc._logo.svg" class="h-6 w-auto border border-gray-200 p-1" /><img src="https://upload.wikimedia.org/wikipedia/commons/2/2a/Mastercard-logo.svg" class="h-6 w-auto border border-gray-200 p-1" /><img src="https://upload.wikimedia.org/wikipedia/commons/3/30/American_Express_logo.svg" class="h-6 w-auto border border-gray-200 p-1" /><img src="https://upload.wikimedia.org/wikipedia/commons/b/b5/PayPal.svg" class="h-6 w-auto border border-gray-200 p-1" /><img src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Apple_logo_black.svg" class="h-6 w-auto border border-gray-200 p-1" /><img src="https://upload.wikimedia.org/wikipedia/commons/2/2a/Google_Pay_Logo.svg" class="h-6 w-auto border border-gray-200 p-1" /><div class="h-6 w-10 border border-gray-200 flex items-center justify-center text-[8px] font-bold">Klarna.</div><div class="h-6 w-10 border border-gray-200 flex items-center justify-center text-[8px] font-bold">afterpay</div></div></div>
            </div>
            <div><h4 class="font-bold text-sm mb-6">Customer Care</h4><ul class="text-xs text-gray-500 space-y-3"><li><a href="#" class="hover:text-black">Contact Us</a></li><li><a href="#" class="hover:text-black">Loyalty Rewards</a></li><li><a href="#" class="hover:text-black">Shipping & Delivery</a></li><li><a href="#" class="hover:text-black">Returns & Exchanges</a></li><li><a href="#" class="hover:text-black">Privacy Policy</a></li></ul></div>
            <div><h4 class="font-bold text-sm mb-6">About Us</h4><ul class="text-xs text-gray-500 space-y-3"><li><a href="#" class="hover:text-black">About NNL</a></li><li><a href="#" class="hover:text-black">Press</a></li></ul></div>
        </div>
        <div class="text-xs text-gray-400 text-center mt-8">&copy; 2025 NNL Clone.</div>
    </div>
  </footer>
</template>
<script setup>defineProps({ showMedia: { type: Boolean, default: true }, showBadges: { type: Boolean, default: true } })</script>