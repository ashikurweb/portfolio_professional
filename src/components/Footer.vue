<template>
    <footer class="py-12 border-t border-white/5 bg-[#070B16]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
                <div class="md:col-span-2">
                    <a href="#" class="flex items-center gap-2 group mb-6">
                        <div
                            class="w-10 h-10 bg-primary rounded-lg flex items-center justify-center rotate-3 group-hover:rotate-0 transition-transform">
                            <span class="text-dark font-bold text-xl">P</span>
                        </div>
                        <span class="text-2xl font-bold tracking-tight">Portfolio</span>
                    </a>
                    <p class="text-gray-500 max-w-sm leading-relaxed">
                        Crafting digital experiences with passion and precision. Let's create something meaningful
                        together.
                    </p>
                </div>

                <div>
                    <h4 class="text-white font-bold mb-6">Quick Links</h4>
                    <ul class="space-y-4">
                        <li v-for="link in links" :key="link.name">
                            <a :href="link.href" class="text-gray-500 hover:text-primary transition-colors">{{ link.name
                                }}</a>
                        </li>
                    </ul>
                </div>

                <div>
                    <h4 class="text-white font-bold mb-6">Social Connect</h4>
                    <div class="flex gap-4">
                        <a href="#"
                            class="w-10 h-10 rounded-full bg-white/5 border border-white/10 flex items-center justify-center text-gray-400 hover:text-primary hover:border-primary transition-all">
                            <i class="fab fa-github"></i>
                        </a>
                        <a href="#"
                            class="w-10 h-10 rounded-full bg-white/5 border border-white/10 flex items-center justify-center text-gray-400 hover:text-primary hover:border-primary transition-all">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#"
                            class="w-10 h-10 rounded-full bg-white/5 border border-white/10 flex items-center justify-center text-gray-400 hover:text-primary hover:border-primary transition-all">
                            <i class="fab fa-linkedin-in"></i>
                        </a>
                    </div>
                </div>
            </div>

            <div
                class="pt-12 border-t border-white/5 flex flex-col md:flex-row justify-between items-center gap-6 text-gray-600 text-sm">
                <p>&copy; 2026 Alex Morgan. All rights reserved.</p>
                <div class="flex gap-8">
                    <a href="#" class="hover:text-white transition-colors">Privacy Policy</a>
                    <a href="#" class="hover:text-white transition-colors">Terms of Service</a>
                </div>
            </div>
        </div>
    </footer>
</template>

<script setup>
const links = [
    { name: 'Home', href: '#' },
    { name: 'About', href: '#about' },
    { name: 'Projects', href: '#projects' },
    { name: 'Skills', href: '#skills' },
]
</script>
