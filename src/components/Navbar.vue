<template>
    <nav ref="navRef" class="fixed top-0 left-0 w-full z-50 overflow-hidden">
        <!-- Main Navbar Content -->
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div ref="containerRef" class="flex justify-between items-center h-24">
                <!-- Logo Section -->
                <div class="flex items-center logo-brand opacity-0">
                    <a href="#" class="block transform hover:scale-105 transition-transform duration-300">
                        <Logo />
                    </a>
                </div>

                <!-- Desktop Navigation -->
                <div class="hidden md:flex items-center gap-10">
                    <nav class="flex gap-8">
                        <a v-for="link in navLinks" :key="link.name" :href="link.href"
                            class="nav-item opacity-0 text-sm font-semibold relative group py-2 transition-colors duration-300"
                            :class="activeSection === link.name ? 'text-primary' : 'text-gray-400 hover:text-primary'">
                            {{ link.name }}
                            <span
                                class="absolute bottom-0 left-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-full"
                                :class="activeSection === link.name ? 'w-full' : 'w-0'"></span>
                        </a>
                    </nav>
                    <div class="hire-btn-wrapper opacity-0">
                        <button ref="hireBtnRef"
                            class="hire-btn-elite relative group px-8 py-3 rounded-full transition-all duration-500">
                            <!-- Always Rotating Border -->
                            <div class="absolute inset-0 rounded-full border border-primary/20"></div>
                            <div class="absolute inset-0 rounded-full overflow-hidden">
                                <div
                                    class="absolute inset-[-100%] bg-[conic-gradient(from_0deg,transparent,var(--color-primary),transparent_30%)] animate-border-spin">
                                </div>
                            </div>

                            <!-- Inner Content Backdrop -->
                            <div class="absolute inset-[1.5px] bg-[#0a0f1e] rounded-full z-10"></div>

                            <!-- Button Content -->
                            <div class="relative z-20 flex items-center gap-3 whitespace-nowrap">
                                <span
                                    class="text-sm font-bold tracking-[0.2em] text-white group-hover:text-primary uppercase transition-colors duration-300">
                                    {{ hireButtonText }}
                                </span>
                                <!-- Small Animated Icon -->
                                <div
                                    class="w-1.5 h-1.5 rounded-full bg-primary animate-pulse shadow-[0_0_8px_var(--color-primary)]">
                                </div>
                            </div>
                        </button>
                    </div>
                </div>

                <!-- Mobile Toggle -->
                <!-- Mobile Toggle Modern -->
                <button @click="isMobileMenuOpen = !isMobileMenuOpen"
                    class="md:hidden relative z-50 p-2 group focus:outline-none" aria-label="Toggle Menu">
                    <!-- Hover Effect Background -->
                    <div
                        class="absolute inset-0 bg-white/5 rounded-full scale-0 group-hover:scale-100 transition-transform duration-300">
                    </div>

                    <div class="relative flex flex-col items-end justify-center gap-1.5 w-8">
                        <span class="h-0.5 bg-white rounded-full transition-all duration-300 group-hover:bg-primary"
                            :class="isMobileMenuOpen ? 'w-8 rotate-45 translate-y-2' : 'w-8'"></span>
                        <span
                            class="h-0.5 bg-white rounded-full transition-all duration-300 group-hover:bg-primary group-hover:w-8"
                            :class="isMobileMenuOpen ? 'w-0 opacity-0' : 'w-5'"></span>
                        <span class="h-0.5 bg-white rounded-full transition-all duration-300 group-hover:bg-primary"
                            :class="isMobileMenuOpen ? 'w-8 -rotate-45 -translate-y-2' : 'w-8'"></span>
                    </div>
                </button>
            </div>
        </div>

        <!-- Mobile Menu Overlay -->
        <Teleport to="body">
            <Transition @enter="enterMenu" @leave="leaveMenu" :css="false">
                <div v-if="isMobileMenuOpen"
                    class="md:hidden fixed inset-0 bg-darker/98 backdrop-blur-2xl z-[40] mobile-menu-overlay">
                    <div class="flex flex-col items-center justify-center h-full gap-10">
                        <a v-for="(link, index) in navLinks" :key="link.name" :href="link.href"
                            @click="isMobileMenuOpen = false"
                            class="mobile-link text-3xl font-black transition-colors transform hover:scale-110 duration-300 opacity-0 translate-y-8"
                            :class="activeSection === link.name ? 'text-primary' : 'text-white hover:text-primary'">
                            <span class="text-primary/30 mr-2 font-mono text-sm">0{{ index + 1 }}</span>
                            {{ link.name }}
                        </a>
                        <button @click="isMobileMenuOpen = false"
                            class="mobile-btn mt-6 bg-primary text-dark font-black py-5 px-12 rounded-xl text-xl shadow-[0_0_30px_rgba(0,210,123,0.3)] opacity-0 translate-y-8">
                            Hire Me
                        </button>
                    </div>
                </div>
            </Transition>
        </Teleport>
    </nav>
</template>

<script setup>
import { onMounted, ref, watch, nextTick } from 'vue'
import Logo from './Logo.vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { TextPlugin } from 'gsap/TextPlugin'

gsap.registerPlugin(ScrollTrigger, TextPlugin)

const navRef = ref(null)
const containerRef = ref(null)
const hireBtnRef = ref(null)
const isMobileMenuOpen = ref(false)
const isScrolled = ref(false)
const hireButtonText = ref('Hire Me')
const isGlitching = ref(false)
const activeSection = ref('Home')

const navLinks = [
    { name: 'Home', href: '#' },
    { name: 'About', href: '#about' },
    { name: 'Projects', href: '#projects' },
    { name: 'Skills', href: '#skills' },
    { name: 'Contact', href: '#contact' },
]

// Prevent scroll when mobile menu is open
watch(isMobileMenuOpen, (val) => {
    document.body.style.overflow = val ? 'hidden' : ''
})

const enterMenu = (el, done) => {
    const tl = gsap.timeline({ onComplete: done })

    tl.fromTo(el,
        { opacity: 0, backdropFilter: 'blur(0px)' },
        { opacity: 1, backdropFilter: 'blur(24px)', duration: 0.5, ease: 'power2.out' }
    )

    const links = el.querySelectorAll('.mobile-link')
    const btn = el.querySelector('.mobile-btn')

    tl.to([...links, btn], {
        opacity: 1,
        y: 0,
        stagger: 0.1,
        duration: 0.8,
        ease: 'elastic.out(1, 0.5)',
        delay: -0.3
    })
}

const leaveMenu = (el, done) => {
    const tl = gsap.timeline({ onComplete: done })

    const links = el.querySelectorAll('.mobile-link')
    const btn = el.querySelector('.mobile-btn')

    tl.to([...links, btn], {
        opacity: 0,
        y: -20,
        stagger: 0.05,
        duration: 0.3,
        ease: 'power2.in'
    })

    tl.to(el, {
        opacity: 0,
        backdropFilter: 'blur(0px)',
        duration: 0.4,
        ease: 'power2.in'
    }, '-=0.1')
}

onMounted(() => {
    const nav = navRef.value
    const container = containerRef.value

    ScrollTrigger.create({
        start: 'top -20',
        onUpdate: (self) => {
            const scrolled = self.scroll() > 20

            if (scrolled !== isScrolled.value) {
                isScrolled.value = scrolled

                if (scrolled) {
                    gsap.to(nav, {
                        backgroundColor: 'rgba(10, 15, 30, 0.85)',
                        backdropFilter: 'blur(24px)',
                        borderBottom: '1px solid rgba(255, 255, 255, 0.1)',
                        boxShadow: '0 15px 40px -15px rgba(0,0,0,0.8)',
                        duration: 0.4,
                        ease: 'expo.out'
                    })
                    gsap.to(container, {
                        height: '75px',
                        duration: 0.4,
                        ease: 'expo.out'
                    })
                } else {
                    gsap.to(nav, {
                        backgroundColor: 'rgba(10, 15, 30, 0)',
                        backdropFilter: 'blur(0px)',
                        borderBottom: '1px solid rgba(255, 255, 255, 0)',
                        boxShadow: 'none',
                        duration: 0.4,
                        ease: 'expo.out'
                    })
                    gsap.to(container, {
                        height: '96px',
                        duration: 0.4,
                        ease: 'expo.out'
                    })
                }
            }
        }
    })

    // Active Link Tracking
    nextTick(() => {
        navLinks.forEach(link => {
            if (link.href === '#') {
                // Home Tracker (Top of page)
                ScrollTrigger.create({
                    trigger: 'body',
                    start: 'top 20%',
                    end: 'top -20%', // Does not really end, but logic handles "Enter Back"
                    onEnter: () => activeSection.value = 'Home',
                    onEnterBack: () => activeSection.value = 'Home'
                })
                return
            }

            const section = document.querySelector(link.href)
            if (section) {
                ScrollTrigger.create({
                    trigger: section,
                    start: 'top 50%',
                    end: 'bottom 50%',
                    onEnter: () => activeSection.value = link.name,
                    onEnterBack: () => activeSection.value = link.name
                })
            }
        })
    })

    // Hire Button Typing Animation
    const phrases = ['Hire Me', 'Let\'s Talk', 'Start Project', 'Get in Touch']
    let currentIndex = 0

    const typePhrase = () => {
        const nextPhrase = phrases[currentIndex]

        // Trigger glitch effect
        isGlitching.value = true

        gsap.timeline()
            .to(hireButtonText, {
                duration: 0.2,
                text: '',
                ease: 'power2.in',
            })
            .to(hireButtonText, {
                duration: 0.6,
                text: nextPhrase,
                ease: 'none',
                onComplete: () => {
                    isGlitching.value = false
                }
            })

        currentIndex = (currentIndex + 1) % phrases.length
    }

    // Entrance Animation on Preloader Complete
    window.addEventListener('preloaderComplete', () => {
        const tl = gsap.timeline({ defaults: { ease: 'expo.out', duration: 1.2 } })

        gsap.set('.nav-item', { y: -20, opacity: 0 })
        gsap.set('.logo-brand', { x: -30, opacity: 0 })
        gsap.set('.hire-btn-wrapper', { scale: 0.8, opacity: 0 })

        tl.to('.logo-brand', { x: 0, opacity: 1 }, "+=0.2")
            .to('.nav-item', { y: 0, opacity: 1, stagger: 0.1 }, "-=0.8")
            .to('.hire-btn-wrapper', { scale: 1, opacity: 1, ease: 'back.out(1.7)' }, "-=0.6")
    })

    // Magnetic Effect for Hire Button
    const hireBtn = hireBtnRef.value
    if (hireBtn) {
        hireBtn.addEventListener('mousemove', (e) => {
            const rect = hireBtn.getBoundingClientRect()
            const x = e.clientX - rect.left - rect.width / 2
            const y = e.clientY - rect.top - rect.height / 2

            gsap.to(hireBtn, {
                x: x * 0.3,
                y: y * 0.3,
                duration: 0.5,
                ease: "power2.out"
            })
        })

        hireBtn.addEventListener('mouseleave', () => {
            gsap.to(hireBtn, {
                x: 0,
                y: 0,
                duration: 1,
                ease: "elastic.out(1, 0.3)"
            })
        })
    }

    // Start animation after 2 seconds, then repeat every 4 seconds
    gsap.delayedCall(2, () => {
        typePhrase()
        setInterval(typePhrase, 4000)
    })
})
</script>

<style scoped>
/* Elite Hire Button Styles */
.hire-btn-elite {
    background: transparent;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.hire-btn-elite:hover {
    box-shadow: 0 0 30px rgba(0, 210, 123, 0.15);
}

@keyframes border-spin {
    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(360deg);
    }
}

.animate-border-spin {
    animation: border-spin 3s linear infinite;
}

.perspective-1000 {
    perspective: 1000px;
}
</style>
