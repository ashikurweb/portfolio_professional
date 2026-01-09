<template>
    <footer class="py-20 bg-[#020408] border-t border-white/5 relative overflow-hidden">
        <!-- Tech Grid Background -->
        <div class="absolute inset-0 z-0 pointer-events-none opacity-20">
            <div
                class="absolute inset-0 bg-[linear-gradient(to_right,#ffffff03_1px,transparent_1px),linear-gradient(to_bottom,#ffffff03_1px,transparent_1px)] bg-[size:40px_40px]">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-6 relative z-10">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-12 mb-20">
                <!-- Brand Column -->
                <div class="space-y-6">
                    <a href="#" class="inline-block group">
                        <Logo class="group-hover:opacity-80 transition-opacity" />
                    </a>
                    <p class="text-gray-400 text-lg leading-relaxed font-light">
                        Architecting digital dominance through precision engineering.
                    </p>
                </div>

                <!-- Navigation Column -->
                <div>
                    <h4 class="text-white font-bold uppercase tracking-widest text-sm mb-8 flex items-center gap-3">
                        <span class="w-2 h-2 rounded-full bg-primary"></span>
                        Navigation
                    </h4>
                    <ul class="space-y-4">
                        <li v-for="link in links" :key="link.name">
                            <a :href="link.href"
                                class="text-gray-500 hover:text-white transition-colors flex items-center gap-2 group">
                                <span class="w-0 h-[1px] bg-primary transition-all duration-300 group-hover:w-4"></span>
                                {{ link.name }}
                            </a>
                        </li>
                    </ul>
                </div>

                <!-- Connect Column (New Home for Icons) -->
                <div>
                    <h4 class="text-white font-bold uppercase tracking-widest text-sm mb-8 flex items-center gap-3">
                        <span class="w-2 h-2 rounded-full bg-primary"></span>
                        Connect
                    </h4>
                    <div class="grid grid-cols-2 gap-4">
                        <a v-for="social in socials" :key="social.name" :href="social.href"
                            class="group relative h-14 bg-white/[0.03] border border-white/5 overflow-hidden flex items-center justify-center transition-all duration-300 hover:border-primary/50 hover:shadow-[0_0_20px_rgba(0,210,123,0.15)]">

                            <!-- Liquid Hover Background -->
                            <div
                                class="absolute inset-0 bg-gradient-to-tr from-primary/20 via-primary/5 to-transparent translate-y-[100%] group-hover:translate-y-0 transition-transform duration-500 ease-out">
                            </div>

                            <!-- Icon & Label -->
                            <div class="relative z-10 flex items-center gap-3">
                                <component :is="social.icon"
                                    class="w-5 h-5 text-gray-400 group-hover:text-white transition-colors" />
                                <span
                                    class="text-xs font-mono font-bold text-gray-500 group-hover:text-white uppercase tracking-wider transition-colors">{{
                                        social.name }}</span>
                            </div>
                        </a>
                    </div>
                </div>
            </div>

            <!-- Bottom Bar -->
            <div
                class="pt-8 border-t border-white/5 flex flex-col md:flex-row justify-between items-center gap-6 text-[10px] font-mono text-gray-600 uppercase tracking-wider">
                <p>&copy; 2026 ASHIKUR RAHMAN. ALL SYSTEMS SECURED.</p>
                <div class="flex gap-8">
                    <a href="#" class="hover:text-primary transition-colors">Privacy_Protocol</a>
                    <a href="#" class="hover:text-primary transition-colors">Term_Of_Service</a>
                </div>
            </div>
        </div>
    </footer>
</template>

<script setup>
import Logo from './Logo.vue'
import { Github, Twitter, Linkedin, Instagram } from 'lucide-vue-next'

const links = [
    { name: 'Home', href: '#' },
    { name: 'About', href: '#about' },
    { name: 'Projects', href: '#projects' },
    { name: 'Skills', href: '#skills' },
    { name: 'Contact', href: '#contact' },
]

const socials = [
    { name: 'Github', href: '#', icon: Github },
    { name: 'Twitter', href: '#', icon: Twitter },
    { name: 'Linkedin', href: '#', icon: Linkedin },
    { name: 'Instagram', href: '#', icon: Instagram },
]
</script>
