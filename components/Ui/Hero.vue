<template>
        <div class="relative bg-cover bg-black bg-center h-screen flex flex-col items-center justify-start py-48 lg:py-72 space-y-10"
                :style="{ backgroundImage: backgroundImageStyle }">

                <h2 class="text-white font-bold text-center text-2xl md:text-5xl text-wrap w-10/12">
                        Don’t miss out!
                        Explore the <span class="text-[#FFE047]">vibrant events</span> happening locally and globally.
                </h2>
                <div class="relative">
                        <!-- Search icon -->
                        <span class="absolute left-3 top-3 text-gray-400">
                                <icon class="iconify" name="bi:search" style="font-size: 1.2rem;"></icon>
                        </span>

                        <!-- Input field -->
                        <input type="text" v-model="searchQuery" @input="handleInput"
                                class="w-80 md:w-96 h-12 pl-10 pr-12 text-lg border-2 border-gray-300 rounded-md focus:outline-none focus:border-blue-500"
                                placeholder="Search..." @keyup.enter="$router.push(`/events?search=${searchQuery}`)" />

                        <!-- Clear button -->
                        <!-- <span v-if="searchQuery" class="absolute right-3 top-3 text-gray-400 cursor-pointer"
                                @click="clearInput">
                                <icon class="iconify" name="bi:x-circle-fill" style="font-size: 1.2rem;"></icon>
                        </span> -->
                        <button type="submit" v-if="searchQuery" @click="$router.push(`/events?search=${searchQuery}`)"
                                class="text-white absolute bg-[#FFE047]  end-2 bottom-1.5   hover:bg-[#2D2C3C] focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-4 py-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                                Search
                        </button>
                </div>
        </div>
</template>

<script setup>
import { ref } from 'vue';

const searchQuery = ref('');

const handleInput = () => {
        // Handle input change
};

const clearInput = () => {
        // Clear input
};

// Background image style
const backgroundImageStyle = ref("url('/HeroImage.png')");

// Watch screen width and change background image and size accordingly
window.addEventListener('resize', () => {
        if (window.innerWidth <= 767) {
                backgroundImageStyle.value = "url('/HeroImage-mobile.png')";
                // Set background size to 290%
                document.querySelector('.bg-cover').style.backgroundSize = '250%';
        } else {
                backgroundImageStyle.value = "url('/HeroImage.png')";
                // Set background size to 170%
                document.querySelector('.bg-cover').style.backgroundSize = '170%';
        }
});

</script>

<style scoped>
/* Additional styles can go here */
</style>

<!-- h-96 bg-[#2D2C3C] flex flex-col items-center justify-center space-y-10 -->