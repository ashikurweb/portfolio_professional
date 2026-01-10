<template>
    <section id="contact" class="py-32 bg-[#020408] relative overflow-hidden" ref="contactRef">
        <!-- Technical Background Grid -->
        <div class="absolute inset-0 z-0 pointer-events-none">
            <div
                class="absolute inset-0 bg-[linear-gradient(to_right,#ffffff03_1px,transparent_1px),linear-gradient(to_bottom,#ffffff03_1px,transparent_1px)] bg-[size:40px_40px] [mask-image:radial-gradient(ellipse_60%_50%_at_50%_0%,#000_70%,transparent_100%)]">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-6 relative z-10">
            <!-- Success Modal -->
            <div v-if="showModal" class="fixed inset-0 z-[9999] flex items-center justify-center px-4 modal-wrapper">
                <div class="absolute inset-0 bg-black/80 backdrop-blur-sm modal-backdrop" @click="closeModal"></div>
                <div
                    class="relative bg-[#0A0F1E] border border-primary/20 p-8 rounded-2xl max-w-md w-full text-center modal-content scale-90 opacity-0">
                    <div class="w-16 h-16 rounded-full bg-primary/10 flex items-center justify-center mx-auto mb-6">
                        <CheckCircle class="w-8 h-8 text-primary" />
                    </div>
                    <h3 class="text-2xl font-black text-white italic uppercase mb-2">Message Sent!</h3>
                    <p class="text-white/60 mb-8 leading-relaxed">
                        Thank you for reaching out. I've received your message and will get back to you as soon as
                        possible.
                    </p>
                    <button @click="closeModal"
                        class="w-full py-4 bg-primary text-black font-bold uppercase tracking-widest rounded-lg hover:bg-white transition-colors">
                        Close
                    </button>
                </div>
            </div>

            <!-- Massive Header -->
            <div class="mb-24 contact-header">
                <div class="flex items-center gap-4 mb-6 reveal-meta opacity-0">
                    <span class="w-12 h-[1px] bg-primary/40"></span>
                    <span
                        class="text-[10px] font-mono font-black text-primary tracking-[0.6em] uppercase animate-pulse">
                        // INITIATE_PROTOCOL
                    </span>
                </div>
                <h2
                    class="text-5xl sm:text-7xl md:text-[8rem] font-black italic uppercase leading-[0.85] tracking-tighter text-white mb-8 perspective-[1000px]">
                    <div class="overflow-hidden"><span class="block reveal-text-contact origin-bottom">LET'S</span>
                    </div>
                    <div class="overflow-hidden"><span class="block text-transparent reveal-text-contact origin-bottom"
                            style="-webkit-text-stroke: 1px rgba(255,255,255,0.2);">BUILD</span></div>
                    <div class="overflow-hidden"><span class="block text-primary reveal-text-contact origin-bottom">THE
                            FUTURE</span></div>
                </h2>
            </div>

            <div class="grid lg:grid-cols-2 gap-20 contact-content">
                <!-- Left: Contact Methods -->
                <div class="space-y-12">
                    <p class="text-xl text-gray-400 leading-relaxed font-light reveal-fade opacity-0">
                        Ready to transform concepts into digital reality? <br />
                        Signal status: <span class="text-green-400 font-mono text-sm tracking-widest uppercase">[ ONLINE
                            ]</span>
                    </p>

                    <div class="grid gap-6">
                        <div v-for="(info, index) in contactInfo" :key="index"
                            class="group relative overflow-hidden border border-white/5 bg-white/[0.02] hover:bg-white/[0.05] p-8 transition-all duration-500 hover:border-primary/30 contact-card opacity-0 translate-y-10">

                            <div
                                class="absolute inset-0 bg-gradient-to-r from-primary/0 via-primary/5 to-primary/0 translate-x-[-100%] group-hover:translate-x-[100%] transition-transform duration-1000">
                            </div>

                            <div class="relative z-10 flex items-center gap-6">
                                <div
                                    class="w-12 h-12 rounded-full border border-primary/20 bg-primary/5 flex items-center justify-center text-primary group-hover:scale-110 group-hover:bg-primary group-hover:text-black transition-all duration-500">
                                    <component :is="info.icon" class="w-5 h-5" />
                                </div>
                                <div>
                                    <div class="text-[10px] uppercase font-mono text-gray-500 tracking-[0.2em] mb-1">{{
                                        info.label }}</div>
                                    <div
                                        class="text-xl font-bold text-white tracking-tight group-hover:text-primary transition-colors">
                                        {{ info.value }}</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Right: High-Tech Form -->
                <div class="relative">
                    <div
                        class="absolute -inset-1 bg-gradient-to-b from-primary/20 to-transparent rounded-[2rem] blur-xl opacity-20">
                    </div>
                    <form @submit.prevent="handleSubmit"
                        class="relative bg-black/40 backdrop-blur-xl border border-white/10 rounded-[2rem] p-8 md:p-12 space-y-8">
                        <div class="grid md:grid-cols-2 gap-8">
                            <div class="group relative form-item opacity-0 translate-y-4">
                                <label
                                    class="text-xs font-mono text-gray-500 tracking-wider uppercase mb-2 block group-focus-within:text-primary transition-colors">Coordinates
                                    [Name]</label>
                                <input v-model="formData.name" type="text"
                                    class="w-full bg-transparent border-b border-white/10 py-3 text-white focus:border-primary focus:outline-none transition-all placeholder:text-white/10 font-light text-lg"
                                    :class="{ 'border-red-500': errors.name }" placeholder="John Doe" />
                                <span v-if="errors.name" class="text-red-500 text-[10px] mt-1 block">{{ errors.name
                                    }}</span>
                            </div>
                            <div class="group relative form-item opacity-0 translate-y-4">
                                <label
                                    class="text-xs font-mono text-gray-500 tracking-wider uppercase mb-2 block group-focus-within:text-primary transition-colors">Communication
                                    Link [Email]</label>
                                <input v-model="formData.email" type="email"
                                    class="w-full bg-transparent border-b border-white/10 py-3 text-white focus:border-primary focus:outline-none transition-all placeholder:text-white/10 font-light text-lg"
                                    :class="{ 'border-red-500': errors.email }" placeholder="john@example.com" />
                                <span v-if="errors.email" class="text-red-500 text-[10px] mt-1 block">{{ errors.email
                                    }}</span>
                            </div>
                        </div>

                        <div class="group relative form-item opacity-0 translate-y-4">
                            <label
                                class="text-xs font-mono text-gray-500 tracking-wider uppercase mb-2 block group-focus-within:text-primary transition-colors">System
                                Header [Subject]</label>
                            <input v-model="formData.subject" type="text"
                                class="w-full bg-transparent border-b border-white/10 py-3 text-white focus:border-primary focus:outline-none transition-all placeholder:text-white/10 font-light text-lg"
                                :class="{ 'border-red-500': errors.subject }" placeholder="Project Proposal" />
                            <span v-if="errors.subject" class="text-red-500 text-[10px] mt-1 block">{{ errors.subject
                                }}</span>
                        </div>

                        <div class="group relative form-item opacity-0 translate-y-4">
                            <label
                                class="text-xs font-mono text-gray-500 tracking-wider uppercase mb-2 block group-focus-within:text-primary transition-colors">Data
                                Payload [Message]</label>
                            <textarea v-model="formData.message" rows="4"
                                class="w-full bg-transparent border-b border-white/10 py-3 text-white focus:border-primary focus:outline-none transition-all placeholder:text-white/10 font-light text-lg resize-none"
                                :class="{ 'border-red-500': errors.message }"
                                placeholder="Tell me about your project..."></textarea>
                            <span v-if="errors.message" class="text-red-500 text-[10px] mt-1 block">{{ errors.message
                                }}</span>
                        </div>

                        <button type="submit" :disabled="isSubmitting"
                            class="w-full group relative px-8 py-5 bg-primary text-black font-bold uppercase tracking-widest overflow-hidden transition-all hover:bg-white hover:text-black disabled:opacity-50 disabled:cursor-not-allowed form-item opacity-0 translate-y-4 rounded-lg">
                            <span class="relative z-10 flex items-center justify-center gap-3">
                                {{ isSubmitting ? 'SENDING...' : 'Send Message' }}
                                <svg v-if="!isSubmitting" xmlns="http://www.w3.org/2000/svg"
                                    class="w-5 h-5 transition-transform group-hover:translate-x-1" fill="none"
                                    viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M14 5l7 7m0 0l-7 7m7-7H3" />
                                </svg>
                                <svg v-else class="animate-spin -ml-1 mr-3 h-5 w-5 text-black"
                                    xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                                    <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor"
                                        stroke-width="4"></circle>
                                    <path class="opacity-75" fill="currentColor"
                                        d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z">
                                    </path>
                                </svg>
                            </span>
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { onMounted, ref, reactive, watch, nextTick } from 'vue'
import { Mail, Phone, MapPin, CheckCircle, XIcon } from 'lucide-vue-next'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)
const contactRef = ref(null)

const contactInfo = [
    { label: 'Secure Channel', value: 'ashikurrahman7194@gmail.com', icon: Mail },
    { label: 'Voice Link', value: '+8801700-917194', icon: Phone },
    { label: 'Base Station', value: 'Dhaka, Bangladesh', icon: MapPin },
]

// Form Logic
const formData = reactive({
    name: '',
    email: '',
    subject: '',
    message: ''
})

const errors = reactive({
    name: '',
    email: '',
    subject: '',
    message: ''
})

const showModal = ref(false)
const isSubmitting = ref(false)

const validateForm = () => {
    let isValid = true
    errors.name = ''
    errors.email = ''
    errors.subject = ''
    errors.message = ''

    if (!formData.name) {
        errors.name = 'Name is required'
        isValid = false
    }

    if (!formData.email) {
        errors.email = 'Email is required'
        isValid = false
    } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
        errors.email = 'Invalid email format'
        isValid = false
    }

    if (!formData.subject) {
        errors.subject = 'Subject is required'
        isValid = false
    }

    if (!formData.message) {
        errors.message = 'Message is required'
        isValid = false
    }

    return isValid
}

const handleSubmit = async () => {
    if (!validateForm()) return

    isSubmitting.value = true

    // Simulate API call
    setTimeout(() => {
        isSubmitting.value = false
        showModal.value = true
        // Reset form
        formData.name = ''
        formData.email = ''
        formData.subject = ''
        formData.message = ''
    }, 1500)
}

const closeModal = () => {
    gsap.to('.modal-content', { scale: 0.9, opacity: 0, duration: 0.3 })
    gsap.to('.modal-backdrop', {
        opacity: 0, duration: 0.3, onComplete: () => {
            showModal.value = false
        }
    })
}

// Watch for modal state to trigger animation
watch(showModal, (val) => {
    if (val) {
        nextTick(() => {
            gsap.fromTo('.modal-backdrop', { opacity: 0 }, { opacity: 1, duration: 0.4 })
            gsap.fromTo('.modal-content',
                { scale: 0.8, opacity: 0, y: 20 },
                { scale: 1, opacity: 1, y: 0, duration: 0.5, ease: 'back.out(1.7)' }
            )
        })
    }
})

onMounted(() => {
    const ctx = gsap.context(() => {

        // 1. Header Text Scrub Animation (Scroll-driven)
        const headerTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.contact-header',
                start: 'top bottom', // Start when header enters view
                end: 'center center', // End when centered
                scrub: 1, // Smooth scrubbing
            }
        })

        headerTl.from('.reveal-text-contact', {
            y: '120%',
            skewY: 10,
            opacity: 0,
            stagger: 0.1,
            duration: 1,
            ease: 'power4.out'
        })
            .from('.reveal-meta', { opacity: 0, duration: 0.5 }, 0)

        // 2. Form & Cards (Auto-play when visible)
        const contentTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.contact-content',
                start: 'top 80%',
                end: 'bottom 10%',
                toggleActions: 'play reverse play reverse'
            }
        })

        // Left Side
        contentTl.to('.reveal-fade', { opacity: 1, y: 0, duration: 0.6 })
            .to('.contact-card', {
                opacity: 1,
                y: 0,
                stagger: 0.1,
                duration: 0.8,
                ease: 'back.out(1.7)'
            }, '-=0.4')

            // Right Side (Form)
            .to('.form-item', {
                opacity: 1,
                y: 0,
                stagger: 0.1,
                duration: 0.8,
                ease: 'power3.out'
            }, '-=0.6')

    }, contactRef.value)
})
</script>
