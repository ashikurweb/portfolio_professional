<template>
    <section id="about" class="py-20 bg-[#0A0F1E]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row items-center gap-16">
                <div class="flex-1">
                    <div class="relative rounded-[2rem] overflow-hidden group">
                        <img src="/assets/about.png" alt="Desk setup"
                            class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700" />
                    </div>
                </div>

                <div class="flex-1">
                    <span class="text-primary font-bold uppercase tracking-widest text-sm mb-4 block">About Me</span>
                    <h2 class="text-4xl md:text-5xl font-bold mb-8 leading-tight">
                        Turning Ideas Into <br />
                        <span class="text-primary">Digital Reality</span>
                    </h2>

                    <p class="text-gray-400 text-lg mb-8 leading-relaxed">
                        With a deep understanding of both design and development, I bridge the gap between aesthetics
                        and functionality. I specialize in creating pixel-perfect, highly interactive web applications
                        that deliver exceptional user experiences.
                    </p>

                    <div class="grid grid-cols-3 gap-8 mb-10">
                        <div v-for="stat in stats" :key="stat.label" class="text-center md:text-left">
                            <div class="text-3xl font-bold text-primary mb-1">{{ stat.value }}</div>
                            <div class="text-xs text-gray-500 uppercase tracking-widest">{{ stat.label }}</div>
                        </div>
                    </div>

                    <button
                        class="bg-[#161B2E] border border-white/10 hover:border-primary/50 text-white font-bold py-4 px-8 rounded-full transition-all group">
                        See My Full Case Studies
                        <span class="inline-block transition-transform group-hover:translate-x-2 ml-2">→</span>
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
const stats = [
    { value: '50+', label: 'Projects Done' },
    { value: '30+', label: 'Happy Clients' },
    { value: '5+', label: 'Years Exp' },
]
</script>
