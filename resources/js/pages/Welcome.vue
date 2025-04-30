<script setup lang="ts">
import { Head } from '@inertiajs/vue3';
import { ChevronDown, ChevronRight, Facebook, Instagram, Linkedin, Mail, Menu as MenuIcon, PhoneCall, TwitterIcon, User, X } from 'lucide-vue-next';
import { ref, onMounted} from 'vue';

import { Autoplay, Navigation } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';
// CSS
import 'swiper/css';
import 'swiper/css/navigation';

const mobileMenuOpen = ref(false);
const openDropdown = ref<string | null>(null);

function toggleDropdown(name: string) {
    openDropdown.value = openDropdown.value === name ? null : name;
}

onMounted(() => {
  // Hide buttons after Swiper initializes
  document.querySelectorAll('.swiper-button-prev, .swiper-button-next')
    .forEach(el => el.style.display = 'none');
});
</script>

<template>
    <Head title="Welcome" />
    <div class="h-screen">
        <section class="bg-teal-700 text-sm text-amber-50">
            <div class="container mx-auto px-4 py-3">
                <div class="flex flex-col items-center justify-between gap-y-4 md:flex-row">
                    <!-- Left: Address and Email -->
                    <div class="flex flex-wrap items-center justify-center gap-x-6 gap-y-2 md:justify-start">
                        <div class="flex items-center space-x-2">
                            <MapPin class="h-4 w-4 text-orange-400" />
                            <p>57 Park Ave, New York</p>
                        </div>
                        <div class="flex items-center space-x-2">
                            <Mail class="h-4 w-4 text-orange-400" />
                            <p>info@example.com</p>
                        </div>
                    </div>

                    <!-- Right: Login, Socials, CTA -->
                    <div class="flex flex-wrap items-center justify-center gap-4 md:justify-end">
                        <!-- Login -->
                        <div class="flex items-center space-x-2">
                            <User class="h-4 w-4 text-white" />
                            <p>Log In</p>
                        </div>

                        <!-- Social Icons with Dividers -->
                        <div class="flex items-center border-l border-white pl-3">
                            <div class="flex space-x-4 divide-x divide-white">
                                <div class="pr-3">
                                    <Facebook
                                        class="h-4 w-4 text-white transition-all duration-300 ease-in-out hover:scale-110 hover:text-orange-500"
                                    />
                                </div>
                                <div class="px-3">
                                    <TwitterIcon
                                        class="h-4 w-4 text-white transition-all duration-300 ease-in-out hover:scale-110 hover:text-orange-500"
                                    />
                                </div>
                                <div class="px-3">
                                    <Instagram
                                        class="h-4 w-4 text-white transition-all duration-300 ease-in-out hover:scale-110 hover:text-orange-500"
                                    />
                                </div>
                                <div class="pl-3">
                                    <Linkedin
                                        class="h-4 w-4 text-white transition-all duration-300 ease-in-out hover:scale-110 hover:text-orange-500"
                                    />
                                </div>
                            </div>
                        </div>

                        <!-- CTA Button -->
                        <div class="border-l border-white pl-3">
                            <button
                                class="inline-flex items-center gap-1 rounded bg-orange-400 px-4 py-2 text-sm text-white transition-all duration-300 ease-in-out hover:-translate-y-0.5 hover:cursor-pointer hover:bg-white hover:text-orange-500 hover:shadow-lg"
                            >
                                Free Consultation
                                <ChevronRight class="h-4 w-4 transition-all duration-300 ease-in-out" />
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <!-- Navigation -->
        <section class="bg-white text-black shadow">
            <div class="container mx-auto flex items-center justify-between px-4 py-4">
                <!-- Logo -->
                <div class="text-xl font-bold tracking-wide">MySite<span class="text-teal-600">.</span></div>

                <!-- Hamburger (Mobile) -->
                <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden">
                    <component :is="mobileMenuOpen ? X : MenuIcon" class="h-6 w-6" />
                </button>

                <!-- Desktop Menu -->
                <nav class="relative hidden items-center space-x-6 text-sm font-medium md:flex">
                    <div class="group relative">
                        <a href="#" class="flex items-center gap-1 hover:text-teal-600">
                            Services <ChevronDown class="h-4 w-4 transition-transform group-hover:rotate-180" />
                        </a>
                        <!-- Dropdown -->
                        <div
                            class="invisible absolute left-0 z-10 mt-2 w-40 rounded-md bg-white opacity-0 shadow-lg transition-all group-hover:visible group-hover:opacity-100"
                        >
                            <a href="#" class="block px-4 py-2 hover:bg-gray-100">Web Design</a>
                            <a href="#" class="block px-4 py-2 hover:bg-gray-100">SEO</a>
                        </div>
                    </div>

                    <a href="#" class="hover:text-teal-600">Home</a>
                    <a href="#" class="hover:text-teal-600">About</a>
                    <a href="#" class="hover:text-teal-600">Blog</a>

                    <div class="group relative">
                        <a href="#" class="flex items-center gap-1 hover:text-teal-600">
                            Pages <ChevronDown class="h-4 w-4 transition-transform group-hover:rotate-180" />
                        </a>
                        <!-- Dropdown -->
                        <div
                            class="invisible absolute left-0 z-10 mt-2 w-40 rounded-md bg-white opacity-0 shadow-lg transition-all group-hover:visible group-hover:opacity-100"
                        >
                            <a href="#" class="block px-4 py-2 hover:bg-gray-100">FAQ</a>
                            <a href="#" class="block px-4 py-2 hover:bg-gray-100">Pricing</a>
                        </div>
                    </div>

                    <a href="#" class="hover:text-teal-600">Contact</a>

                    <!-- Contact Info -->
                    <div class="flex items-center space-x-2 border-l border-gray-300 pl-4">
                        <PhoneCall class="h-4 w-4 text-orange-400" />
                        <span>+123-7767-8989</span>
                    </div>
                </nav>
            </div>

            <!-- Mobile Menu -->
            <div v-if="mobileMenuOpen" class="space-y-2 bg-white px-4 pb-4 text-sm md:hidden">
                <a href="#" class="block">Home</a>
                <a href="#" class="block">About</a>
                <div>
                    <button @click="toggleDropdown('services')" class="flex w-full items-center justify-between">
                        Services <ChevronDown :class="['h-4 w-4 transition-transform', openDropdown === 'services' && 'rotate-180']" />
                    </button>
                    <div v-if="openDropdown === 'services'" class="mt-1 space-y-1 pl-4">
                        <a href="#" class="block">Web Design</a>
                        <a href="#" class="block">SEO</a>
                    </div>
                </div>
                <a href="#" class="block">Blog</a>
                <div>
                    <button @click="toggleDropdown('pages')" class="flex w-full items-center justify-between">
                        Pages <ChevronDown :class="['h-4 w-4 transition-transform', openDropdown === 'pages' && 'rotate-180']" />
                    </button>
                    <div v-if="openDropdown === 'pages'" class="mt-1 space-y-1 pl-4">
                        <a href="#" class="block">FAQ</a>
                        <a href="#" class="block">Pricing</a>
                    </div>
                </div>
                <a href="#" class="block">Contact</a>
                <div class="border-t pt-2 text-sm">
                    <div class="mt-2 flex items-center gap-2">
                        <PhoneCall class="h-4 w-4 text-orange-400" />
                        <span>+123-7767-8989</span>
                    </div>
                </div>
            </div>
        </section>
        <!-- Hero Section -->
        <section>
            <div class="container mx-auto px-4 py-10">
                <!-- Hero Content -->
                <div class="flex flex-col-reverse items-center justify-between gap-10 md:flex-row">
                    <!-- Left Text -->
                    <div class="w-full text-center md:w-2/5 md:text-left">
                        <p class="font-mono text-sm font-bold text-teal-600 uppercase">Top Financial Advisor</p>
                        <h2 class="pt-4 pb-4 font-mono text-4xl leading-tight font-extrabold text-black md:text-6xl">Achieve Your Financial Goals</h2>
                        <p class="font-sans text-base font-light text-black">
                            Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid natus debitis odio dicta sit?
                        </p>
                    </div>

                    <!-- Right Image -->
                    <div class="w-full md:w-3/5">
                        <div class="h-72 w-full rounded-2xl bg-gray-500 md:h-[500px]"></div>
                    </div>
                </div>

                <!-- Bottom Text -->
                <div class="px-4 py-10">
                    <p class="text-center text-base text-black">Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur, magni?</p>
                </div>

                <!-- Carousel Section -->
                <div class="mt-2">
                    <Swiper
                        :modules="[Autoplay, Navigation]"
                        :slides-per-view="5"
                        :space-between="20"
                        :loop="true"
                        :autoplay="{ delay: 1500, disableOnInteraction: false }"
                        :breakpoints="{
                            768: { slidesPerView: 2 },
                            1024: { slidesPerView: 7 },
                        }"
                        navigation
                        class="mySwiper"
                    >
                        <SwiperSlide v-for="n in 20" :key="n">
                            <div class="flex h-20 w-50 items-center justify-center rounded-xl bg-gray-200">
                                <span class="text-3xl font-semibold">{{ n }}</span>
                            </div>
                        </SwiperSlide>
                    </Swiper>
                </div>
            </div>
        </section>
    </div>
    <div class="h-screen">
        <section>
            <div class="container mx-auto px-4 py-10 justify-center items-center">
                <p class="font-mono text-sm font-bold text-teal-600 text-center uppercase">FEATURES THAT YOU WILL LOVE </p>
                <h2 class="w-1/2 m-auto pt-4 pb-4 font-mono text-sm leading-tight font-extrabold text-black md:text-6xl">We Automate Finances To Help Visionaries Scale </h2>
            </div>
        </section>
    </div>
</template>
