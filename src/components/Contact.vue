<template>
    <section id="contact" class="py-20 bg-[#070B16]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="bg-[#0A0F1E] rounded-[3rem] p-8 md:p-16 border border-white/5 relative overflow-hidden">
                <!-- Decoration -->
                <div class="absolute -bottom-20 -right-20 w-80 h-80 bg-primary/10 rounded-full blur-[100px]"></div>

                <div class="flex flex-col lg:flex-row gap-16 relative">
                    <div class="flex-1">
                        <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold mb-8">Let's Work <span
                                class="text-primary">Together</span></h2>
                        <p class="text-gray-400 mb-10 text-lg">
                            Have a project in mind? Reach out and let's build something extraordinary together. I'm
                            always open to new opportunities.
                        </p>

                        <div class="space-y-6">
                            <div v-for="info in contactInfo" :key="info.label" class="flex gap-4 items-start group">
                                <div
                                    class="w-12 h-12 rounded-2xl bg-white/5 border border-white/10 flex items-center justify-center text-primary group-hover:bg-primary group-hover:text-dark transition-all">
                                    <component :is="info.icon" class="w-6 h-6" />
                                </div>
                                <div>
                                    <div class="text-xs uppercase font-bold text-gray-500 tracking-widest mb-1">{{
                                        info.label }}</div>
                                    <div class="text-lg font-medium">{{ info.value }}</div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="flex-[1.2]">
                        <form @submit.prevent class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div>
                                <input type="text" placeholder="Your Name"
                                    class="w-full bg-white/5 border border-white/10 rounded-2xl p-4 focus:ring-2 focus:ring-primary focus:border-transparent outline-none transition-all placeholder:text-gray-600" />
                            </div>
                            <div>
                                <input type="email" placeholder="Email Address"
                                    class="w-full bg-white/5 border border-white/10 rounded-2xl p-4 focus:ring-2 focus:ring-primary focus:border-transparent outline-none transition-all placeholder:text-gray-600" />
                            </div>
                            <div class="md:col-span-2">
                                <input type="text" placeholder="Subject"
                                    class="w-full bg-white/5 border border-white/10 rounded-2xl p-4 focus:ring-2 focus:ring-primary focus:border-transparent outline-none transition-all placeholder:text-gray-600" />
                            </div>
                            <div class="md:col-span-2">
                                <textarea rows="5" placeholder="Project Details"
                                    class="w-full bg-white/5 border border-white/10 rounded-2xl p-4 focus:ring-2 focus:ring-primary focus:border-transparent outline-none transition-all placeholder:text-gray-600 resize-none"></textarea>
                            </div>
                            <div class="md:col-span-2">
                                <button
                                    class="w-full bg-primary hover:bg-primary/90 text-dark font-bold py-5 rounded-2xl shadow-xl shadow-primary/20 transition-all hover:scale-[1.02] active:scale-95 text-lg">
                                    Send Message
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { Mail, Phone, MapPin } from 'lucide-vue-next'

const contactInfo = [
    { label: 'Email', value: 'hello@alexmorgan.com', icon: Mail },
    { label: 'Phone', value: '+1 (555) 000-0000', icon: Phone },
    { label: 'Location', value: 'San Francisco, CA', icon: MapPin },
]
</script>
