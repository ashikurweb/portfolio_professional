<template>
    <nav ref="navRef" class="fixed top-0 left-0 w-full z-50 overflow-hidden">
        <!-- Main Navbar Content -->
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div ref="containerRef" class="flex justify-between items-center h-24">
                <!-- Logo Section -->
                <div class="flex items-center">
                    <a href="#" class="block transform hover:scale-105 transition-transform duration-300">
                        <Logo />
                    </a>
                </div>

                <!-- Desktop Navigation -->
                <div class="hidden md:flex items-center gap-10">
                    <nav class="flex gap-8">
                        <a v-for="link in navLinks" :key="link.name" :href="link.href"
                            class="text-sm font-semibold text-gray-400 hover:text-primary relative group py-2 transition-colors duration-300">
                            {{ link.name }}
                            <span
                                class="absolute bottom-0 left-0 w-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-full"></span>
                        </a>
                    </nav>
                    <button ref="hireBtnRef" class="hire-btn-modern relative group perspective-1000">
                        <!-- Animated Border Gradient -->
                        <div
                            class="absolute inset-0 rounded-full bg-gradient-to-r from-primary via-secondary to-primary bg-[length:200%_100%] animate-gradient-shift opacity-70 group-hover:opacity-100 transition-opacity">
                        </div>
                        <div class="absolute inset-[2px] rounded-full bg-dark z-10"></div>

                        <!-- Button Content -->
                        <span
                            class="relative z-20 block px-8 py-3 font-black text-primary group-hover:text-white transition-colors duration-300">
                            <span class="hire-text-wrapper inline-block" :class="{ 'glitch-active': isGlitching }">
                                {{ hireButtonText }}
                            </span>
                        </span>

                        <!-- Hover Glow Effect -->
                        <div
                            class="absolute inset-0 rounded-full bg-primary/20 blur-xl scale-0 group-hover:scale-150 transition-transform duration-700 -z-10">
                        </div>
                    </button>
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
            <Transition name="fade">
                <div v-if="isMobileMenuOpen" class="md:hidden fixed inset-0 bg-darker/98 backdrop-blur-2xl z-[40]">
                    <div class="flex flex-col items-center justify-center h-full gap-10">
                        <a v-for="(link, index) in navLinks" :key="link.name" :href="link.href"
                            @click="isMobileMenuOpen = false"
                            class="text-3xl font-black text-white hover:text-primary transition-colors transform hover:scale-110 duration-300">
                            <span class="text-primary/30 mr-2 font-mono text-sm">0{{ index + 1 }}</span>
                            {{ link.name }}
                        </a>
                        <button @click="isMobileMenuOpen = false"
                            class="mt-6 bg-primary text-dark font-black py-5 px-12 rounded-xl text-xl shadow-[0_0_30px_rgba(0,210,123,0.3)]">
                            Hire Me
                        </button>
                    </div>
                </div>
            </Transition>
        </Teleport>
    </nav>
</template>

<script setup>
import { onMounted, ref, watch } from 'vue'
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

    // Start animation after 2 seconds, then repeat every 4 seconds
    gsap.delayedCall(2, () => {
        typePhrase()
        gsap.ticker.add(() => { }, 4)
        setInterval(typePhrase, 4000)
    })
})
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.4s ease, transform 0.4s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}

/* Modern Hire Button Styles */
.hire-btn-modern {
    transition: transform 0.3s cubic-bezier(0.23, 1, 0.32, 1);
}

.hire-btn-modern:hover {
    transform: translateY(-2px) scale(1.05);
}

.hire-btn-modern:active {
    transform: translateY(0) scale(0.98);
}

/* Animated Gradient Shift */
@keyframes gradient-shift {
    0% {
        background-position: 0% 50%;
    }

    50% {
        background-position: 100% 50%;
    }

    100% {
        background-position: 0% 50%;
    }
}

.animate-gradient-shift {
    animation: gradient-shift 3s ease infinite;
}

/* Glitch Effect */
.glitch-active {
    animation: glitch 0.3s ease;
}

@keyframes glitch {
    0% {
        transform: translate(0);
    }

    20% {
        transform: translate(-2px, 2px);
    }

    40% {
        transform: translate(-2px, -2px);
    }

    60% {
        transform: translate(2px, 2px);
    }

    80% {
        transform: translate(2px, -2px);
    }

    100% {
        transform: translate(0);
    }
}

.perspective-1000 {
    perspective: 1000px;
}
</style>
