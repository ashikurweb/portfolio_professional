<template>
    <div class="flex items-center gap-3 group cursor-pointer">
        <div class="relative w-12 h-12 flex items-center justify-center">
            <!-- Background Glow -->
            <div
                class="absolute inset-0 bg-primary/20 blur-xl rounded-full scale-0 group-hover:scale-150 transition-transform duration-500">
            </div>

            <!-- Logo SVG -->
            <svg viewBox="0 0 100 100"
                class="w-full h-full relative z-10 transform transition-transform duration-500 group-hover:rotate-[360deg]"
                fill="none" xmlns="http://www.w3.org/2000/svg">
                <!-- Outer Circle / Ring -->
                <circle cx="50" cy="50" r="45" stroke="currentColor" stroke-width="2" class="text-white/10" />

                <!-- Main 'A' Shape -->
                <path d="M30 75 L50 25 L70 75" stroke="url(#logo-gradient)" stroke-width="12" stroke-linecap="round"
                    stroke-linejoin="round" />

                <!-- Inner Bridge / Bar -->
                <path d="M40 60 L60 60" stroke="white" stroke-width="8" stroke-linecap="round"
                    class="group-hover:translate-x-1 transition-transform" />

                <!-- Secondary Accent -->
                <circle cx="50" cy="25" r="6" fill="var(--color-secondary)" class="animate-pulse" />

                <defs>
                    <linearGradient id="logo-gradient" x1="0%" y1="0%" x2="100%" y2="100%">
                        <stop offset="0%" style="stop-color: var(--color-primary); stop-opacity: 1" />
                        <stop offset="100%" style="stop-color: #00A3FF; stop-opacity: 1" />
                    </linearGradient>
                </defs>
            </svg>
        </div>

        <div class="flex flex-col leading-none">
            <span class="text-2xl font-black tracking-tighter uppercase group-hover:text-primary transition-colors">
                Ashikur<span class="text-primary group-hover:text-white">.</span>
            </span>
            <span class="text-[10px] uppercase tracking-[0.4em] font-bold text-gray-500">Developer</span>
        </div>
    </div>
</template>

<style scoped>
svg {
    filter: drop-shadow(0 0 8px rgba(0, 210, 123, 0.3));
}
</style>
