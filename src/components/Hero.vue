<script setup lang="ts">
import heroImage from '../images/malga.jpeg';

defineProps<{
  title: string;
  subtitle: string;
  description?: string;
}>();
</script>

<template>
  <section class="relative h-screen">
    <div class="absolute inset-0">
      <img :src="heroImage" class="w-full h-full object-cover" :alt="title">
      <div class="absolute inset-0 bg-gradient-to-b from-black/20 via-black/50 to-black/70"></div>
    </div>

    <div class="relative h-full flex flex-col items-center justify-center text-center px-4 sm:px-6 lg:px-8">
      <div class="max-w-3xl">
        <p class="text-xs font-bold tracking-[3px] uppercase text-farm-200 mb-4">Agriturismo · Dal 2023</p>
        <h1 class="text-4xl font-extrabold tracking-tight text-white sm:text-5xl lg:text-6xl drop-shadow-lg">
          {{ title }}
        </h1>
        <img
          class="mx-auto my-6"
          src="/new_logo.png"
          alt="Malga Biancoia Logo"
          style="height: 130px; width: auto;"
        />
        <div class="w-12 h-px bg-farm-300 mx-auto mb-6 opacity-80"></div>
        <p class="text-lg text-white/90 leading-relaxed drop-shadow mb-8 max-w-2xl mx-auto">
          {{ subtitle }}
        </p>
        <div class="flex justify-center">
          <a
            href="#menu"
            class="inline-block border border-white/60 hover:border-white text-white font-medium px-8 py-3 rounded-sm text-sm tracking-widest uppercase transition-all duration-200 hover:-translate-y-0.5"
          >
            Scopri il menu
          </a>
        </div>
      </div>
    </div>

    <!-- Scroll hint -->
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-white/50">
      <span class="text-[10px] tracking-[2px] uppercase">Scorri</span>
      <div class="w-4 h-4 border-r border-b border-farm-300/60 rotate-45 animate-bounce"></div>
    </div>
  </section>
</template>
