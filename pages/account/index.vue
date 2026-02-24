<script setup>
import { ref, computed, reactive } from 'vue'
import { useRouter, useRoute } from 'vue-router'

const router = useRouter()
const route = useRoute()

const currentKey = computed(() => route.query.a || 'orders')

const user = ref({ name: 'NINI', email: 'nnl.at27@gmail.com' })

const menuItems = [
    { label: 'My Orders', key: 'orders' },
    { label: 'Address Book', key: 'address-book' },
    { label: 'Loyalty Program', key: 'loyalty' },
    { label: 'Account Details', key: 'details' },
    { label: 'Wish List', key: 'wishlist' },
    { label: 'Reset Password', key: 'password' },
]

const editForm = reactive({
    country: 'Taiwan',
    firstName: 'NINI',
    lastName: 'LIAO',
    address: '',
    apartment: '',
    city: '',
    zip: '',
    phone: ''
})

const countries = ['Taiwan', 'United States', 'United Kingdom', 'Japan', 'France', 'Italy', 'Germany', 'South Korea']

const handleLogout = () => { router.push('/account/login') }
const cancelEdit = () => { router.push({ query: { a: 'address-book' } }) }
const saveAddress = () => { router.push({ query: { a: 'address-book' } }) }
</script>

<template>
  <div>
    <div class="relative h-[30vh] bg-gray-200 flex items-center pl-8 md:pl-20">
        <img src="https://images.unsplash.com/photo-1503342217505-b0815a046baf?w=2000&q=80" class="absolute inset-0 w-full h-full object-cover opacity-80" />
        <h1 class="relative z-10 text-3xl md:text-4xl text-white font-serif tracking-wide drop-shadow-md">My Account</h1>
    </div>

    <div class="max-w-[1920px] mx-auto px-6 md:px-12 py-16 grid grid-cols-1 lg:grid-cols-4 gap-16">
        <div class="lg:col-span-1">
            <div class="mb-10">
                <h2 class="font-bold text-lg uppercase tracking-widest mb-1">{{ user.name }}</h2>
                <p class="text-xs text-gray-500">{{ user.email }}</p>
            </div>
            <nav class="space-y-6">
                <NuxtLink v-for="item in menuItems" :key="item.key" :to="{ query: { a: item.key } }" class="block text-sm transition-colors cursor-pointer" :class="currentKey === item.key || (currentKey === 'edit-address' && item.key === 'address-book') ? 'text-black font-bold border-b border-black pb-1 inline-block' : 'text-gray-400 hover:text-black'">{{ item.label }}</NuxtLink>
                <div @click="handleLogout" class="cursor-pointer text-sm text-gray-400 hover:text-black mt-8 pt-8 border-t border-gray-100">Log Out</div>
            </nav>
        </div>

        <div class="lg:col-span-3">
            <div v-if="currentKey === 'orders'">
                <h3 class="text-sm font-bold uppercase tracking-widest mb-8">My Orders</h3>
                <div class="flex flex-col items-center justify-center py-24 border-t border-gray-100">
                    <svg class="w-8 h-8 text-gray-300 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg>
                    <p class="text-xs text-gray-500 mb-6">No orders</p>
                    <NuxtLink to="/" class="border border-black px-8 py-3 text-xs font-bold uppercase tracking-widest hover:bg-black hover:text-white transition-colors">Shop now</NuxtLink>
                </div>
            </div>

            <div v-else-if="currentKey === 'address-book'">
                <div class="flex justify-between items-end mb-4">
                    <h2 class="text-lg font-normal">Address Book</h2>
                    <NuxtLink :to="{ query: { a: 'edit-address' } }" class="text-xs border-b border-black pb-0.5 hover:opacity-70 transition-opacity">Add New Address</NuxtLink>
                </div>
                <div class="border-b border-dashed border-gray-200 mb-8"></div>
                <div class="flex justify-between items-start mb-8">
                    <div class="text-sm"><p class="font-bold uppercase tracking-widest mb-1">NINI LIAO</p><p class="text-gray-500">Taiwan</p></div>
                    <div class="text-right flex flex-col items-end gap-2">
                         <div class="flex gap-4 text-xs text-gray-400 underline decoration-gray-300"><NuxtLink :to="{ query: { a: 'edit-address', id: '11739919057215' } }" class="hover:text-black hover:decoration-black transition-colors">Edit</NuxtLink><button class="hover:text-black hover:decoration-black transition-colors">Delete</button></div>
                         <span class="text-[10px] text-gray-900 font-medium mt-1">Default</span>
                    </div>
                </div>
                <div class="border-b border-dashed border-gray-200"></div>
            </div>

            <div v-else-if="currentKey === 'edit-address'">
                <h2 class="text-lg font-normal mb-8">Edit Address</h2>
                <form @submit.prevent="saveAddress" class="max-w-2xl">
                    <div class="border-b border-dashed border-gray-200 mb-8"></div>
                    <div class="mb-8">
                        <label class="block text-sm mb-2">Country / Region*</label>
                        <div class="relative">
                            <select v-model="editForm.country" class="w-full bg-transparent border-b border-dashed border-gray-300 py-2 focus:outline-none focus:border-black transition-colors appearance-none cursor-pointer">
                                <option v-for="country in countries" :key="country" :value="country">{{ country }}</option>
                            </select>
                            <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"><svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg></div>
                        </div>
                    </div>
                    <div class="mb-8">
                         <label class="block text-sm mb-2">First Name*</label><input v-model="editForm.firstName" type="text" class="w-full bg-transparent border-b border-dashed border-gray-300 py-2 focus:outline-none focus:border-black transition-colors mb-8" />
                         <label class="block text-sm mb-2">Last Name*</label><input v-model="editForm.lastName" type="text" class="w-full bg-transparent border-b border-dashed border-gray-300 py-2 focus:outline-none focus:border-black transition-colors" />
                    </div>
                    <div class="mb-8"><label class="block text-sm mb-2">Address*</label><input v-model="editForm.address" type="text" class="w-full bg-transparent border-b border-dashed border-gray-300 py-2 focus:outline-none focus:border-black transition-colors" /></div>
                    <div class="mb-8"><label class="block text-sm mb-2">Apartment, suite, etc.(optional)</label><input v-model="editForm.apartment" type="text" class="w-full bg-transparent border-b border-dashed border-gray-300 py-2 focus:outline-none focus:border-black transition-colors" /></div>
                    <div class="mb-8"><label class="block text-sm mb-2">City*</label><input v-model="editForm.city" type="text" class="w-full bg-transparent border-b border-dashed border-gray-300 py-2 focus:outline-none focus:border-black transition-colors" /></div>
                    <div class="mb-8"><label class="block text-sm mb-2">Postal / Zip Code*</label><input v-model="editForm.zip" type="text" class="w-full bg-transparent border-b border-dashed border-gray-300 py-2 focus:outline-none focus:border-black transition-colors" /></div>
                    <div class="mb-12"><label class="block text-sm mb-2">Phone*</label><input v-model="editForm.phone" type="text" class="w-full bg-transparent border-b border-dashed border-gray-300 py-2 focus:outline-none focus:border-black transition-colors" /></div>
                    <div class="flex gap-4 mb-8">
                        <button type="button" @click="cancelEdit" class="flex-1 border border-black py-3 text-sm hover:bg-gray-50 transition-colors uppercase tracking-widest">Cancel</button>
                        <button type="submit" class="flex-1 bg-[#0B1215] text-white py-3 text-sm hover:bg-black transition-colors uppercase tracking-widest">Save</button>
                    </div>
                    <div class="flex items-center justify-center gap-2 cursor-pointer mb-12">
                        <div class="w-5 h-5 rounded-full border border-gray-300 flex items-center justify-center"><svg class="w-3 h-3 text-transparent" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg></div>
                        <span class="text-sm">Set as default address</span>
                    </div>
                </form>
            </div>
            
            <div v-else-if="currentKey === 'details'">
                <div class="flex justify-between items-end mb-4">
                    <h2 class="text-lg font-normal">Account Details</h2>
                    <button class="text-xs border-b border-black pb-0.5 hover:opacity-70 transition-opacity">Edit</button>
                </div>
                <div class="border-b border-dashed border-gray-200 mb-8"></div>
                
                <div class="mb-8">
                    <p class="text-sm mb-2">First Name</p>
                    <p class="text-sm text-gray-500 uppercase">NINI</p>
                </div>
                <div class="border-b border-dashed border-gray-200 mb-8"></div>

                <div class="mb-8">
                    <p class="text-sm mb-2">Last Name</p>
                    <p class="text-sm text-gray-500 uppercase">LIAO</p>
                </div>
                <div class="border-b border-dashed border-gray-200 mb-8"></div>

                <div class="mb-8">
                    <p class="text-sm mb-2">Email Subscription</p>
                    <p class="text-sm text-gray-500">Subscription</p>
                </div>
                <div class="border-b border-dashed border-gray-200"></div>
            </div>

            <div v-else-if="currentKey === 'wishlist'">
                 <h3 class="text-sm font-bold uppercase tracking-widest mb-8">Wish List</h3>
                 <div class="flex flex-col items-center justify-center py-24">
                     <svg class="w-6 h-6 text-gray-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"></path></svg>
                     <p class="text-xs text-gray-500 mb-6">Your Wishlist is currently empty</p>
                     <NuxtLink to="/" class="border border-gray-300 px-8 py-3 text-xs font-bold uppercase tracking-widest hover:border-black transition-colors">Shop Now</NuxtLink>
                 </div>
            </div>

            <div v-else-if="currentKey === 'password'">
                <h3 class="text-sm font-bold uppercase tracking-widest mb-8">Reset Password</h3>
                <div class="max-w-md">
                    <p class="text-sm font-bold mb-2">Send link to Email</p>
                    <p class="text-[10px] text-gray-400 mb-6">We'll send you an email with a link to create a new password</p>
                    <p class="text-sm text-gray-500 mb-8">{{ user.email }}</p>
                    <button class="w-full border border-gray-300 py-3 text-xs font-bold uppercase tracking-widest hover:bg-black hover:text-white transition-colors">Send reset link</button>
                </div>
            </div>

            <div v-else>
                <h3 class="text-sm font-bold uppercase tracking-widest mb-8">{{ menuItems.find(i => i.key === currentKey)?.label }}</h3>
                <p class="text-xs text-gray-400">Content coming soon...</p>
            </div>
        </div>
    </div>
  </div>
</template>
<style scoped></style>