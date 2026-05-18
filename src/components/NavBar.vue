<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline';

const navigation = [
  { name: 'Home', href: '#home' },
  { name: 'Menu', href: '#menu' },
  { name: 'Itinerari', href: '#itinerary' },
  { name: 'News', href: '#news' },
  { name: 'Galleria', href: '#gallery' },
];

const isOpen = ref(false);
const isScrolled = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

onMounted(() => window.addEventListener('scroll', handleScroll));
onUnmounted(() => window.removeEventListener('scroll', handleScroll));
</script>

<template>
  <nav
    class="fixed w-full z-50 transition-all duration-300"
    :class="isScrolled ? 'bg-white shadow-lg' : 'bg-black/40 backdrop-blur-sm'"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-16">
        <div class="flex items-center gap-2">
          <img class="h-10 w-auto" src="/new_logo.png" alt="Malga Biancoia Logo" />
          <span
            class="text-xl font-bold transition-colors duration-300"
            :class="isScrolled ? 'text-farm-600' : 'text-white'"
          >Malga Biancoia</span>
        </div>
        <div class="hidden sm:ml-6 sm:flex sm:space-x-8">
          <a
            v-for="item in navigation"
            :key="item.name"
            :href="item.href"
            class="inline-flex items-center px-1 pt-1 text-sm font-medium transition-colors duration-300"
            :class="isScrolled ? 'text-gray-700 hover:text-farm-500' : 'text-white/90 hover:text-white'"
          >
            {{ item.name }}
          </a>
        </div>
        <div class="-mr-2 flex items-center sm:hidden">
          <button
            @click="isOpen = !isOpen"
            class="inline-flex items-center justify-center p-2 rounded-md transition-colors"
            :class="isScrolled ? 'text-gray-400 hover:text-gray-500 hover:bg-gray-100' : 'text-white hover:bg-white/10'"
          >
            <Bars3Icon v-if="!isOpen" class="block h-6 w-6" />
            <XMarkIcon v-else class="block h-6 w-6" />
          </button>
        </div>
      </div>
    </div>

    <div v-show="isOpen" class="sm:hidden bg-white">
      <div class="pt-2 pb-3 space-y-1">
        <a
          v-for="item in navigation"
          :key="item.name"
          :href="item.href"
          @click="isOpen = false"
          class="block pl-3 pr-4 py-2 text-base font-medium text-gray-700 hover:text-farm-500 hover:bg-gray-50"
        >
          {{ item.name }}
        </a>
      </div>
    </div>
  </nav>
</template>
