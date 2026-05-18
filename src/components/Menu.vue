<script setup lang="ts">
import { ref } from 'vue';
import { ChevronDownIcon } from '@heroicons/vue/24/outline';
import antipastiImage from '../images/menu/antipasti.jpg';
import primiImage from '../images/menu/primi.jpg';
import secondiImage from '../images/menu/secondi.jpg';
import dolciImage from '../images/menu/dolci.jpg';

interface MenuItem {
  name: string;
  price?: string;
}

interface MenuCategory {
  id: string;
  title: string;
  image: string;
  items: MenuItem[];
}

const menu: MenuCategory[] = [
  {
    id: 'antipasti',
    title: 'Antipasti',
    image: antipastiImage,
    items: [
      { name: 'Panino con salame e/o formaggio' },
      { name: 'Tagliere di Formaggi' },
      { name: 'Tagliere di Salumi' },
      { name: 'Tagliere Misto' }
    ]
  },
  {
    id: 'primi',
    title: 'Primi',
    image: primiImage,
    items: [
      { name: 'Gnocchi al Burro di Malga' },
      { name: 'Gnocchi al Ragù di Sorana' },
      { name: 'Lasagne al Ragù di Sorana' }
    ]
  },
  {
    id: 'secondi',
    title: 'Secondi',
    image: secondiImage,
    items: [
      { name: 'Tosella con Polenta e Funghi' },
      { name: 'Hamburger Biancoia' },
      { name: 'Piatto del giorno' }
    ]
  },
  {
    id: 'dolci',
    title: 'Dolci',
    image: dolciImage,
    items: [
      { name: 'Panna Cotta' },
      { name: 'AgriGelato' },
      { name: 'Dolce della Casa' }
    ]
  }
];

const activeCategory = ref<string | null>(null);

const toggleCategory = (categoryId: string) => {
  activeCategory.value = activeCategory.value === categoryId ? null : categoryId;
};

const isActive = (categoryId: string) => activeCategory.value === categoryId;
</script>

<template>
  <section id="menu" class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-bold text-center text-gray-900 mb-2">Menu</h2>
      <p class="text-center text-gray-500 mb-12 text-sm">Cucina tradizionale con prodotti della nostra malga</p>

      <div class="space-y-4">
        <div
          v-for="category in menu"
          :key="category.id"
          class="bg-white rounded-lg shadow-sm overflow-hidden border border-gray-100"
        >
          <!-- Category Header -->
          <button
            @click="toggleCategory(category.id)"
            class="w-full flex items-center justify-between p-5 focus:outline-none focus:ring-2 focus:ring-farm-500 focus:ring-inset"
            :aria-expanded="isActive(category.id)"
            :aria-controls="`content-${category.id}`"
          >
            <div class="flex items-center space-x-4">
              <img
                :src="category.image"
                :alt="category.title"
                class="w-14 h-14 object-cover rounded-lg"
              >
              <h3 class="text-lg font-semibold text-gray-900">{{ category.title }}</h3>
            </div>
            <ChevronDownIcon
              class="w-5 h-5 text-farm-500 transition-transform duration-300"
              :class="{ 'rotate-180': isActive(category.id) }"
            />
          </button>

          <!-- Category Content with transition -->
          <Transition
            enter-active-class="transition-all duration-300 ease-out"
            enter-from-class="opacity-0 max-h-0"
            enter-to-class="opacity-100 max-h-96"
            leave-active-class="transition-all duration-200 ease-in"
            leave-from-class="opacity-100 max-h-96"
            leave-to-class="opacity-0 max-h-0"
          >
            <div
              v-show="isActive(category.id)"
              :id="`content-${category.id}`"
              class="border-t border-gray-100 overflow-hidden"
            >
              <ul class="divide-y divide-gray-100">
                <li
                  v-for="item in category.items"
                  :key="item.name"
                  class="px-6 py-4 flex justify-between items-center hover:bg-farm-50 transition-colors"
                >
                  <span class="text-gray-800 font-medium">{{ item.name }}</span>
                  <span v-if="item.price" class="text-farm-600 font-semibold text-sm">{{ item.price }}</span>
                  <span v-else class="text-gray-400 text-xs italic">su richiesta</span>
                </li>
              </ul>
            </div>
          </Transition>
        </div>
      </div>

      <p class="text-center text-gray-400 text-xs mt-8">
        I piatti possono variare in base alla disponibilità stagionale · Per allergie e intolleranze chiedere al personale
      </p>
    </div>
  </section>
</template>

<style scoped>
.rotate-180 {
  transform: rotate(180deg);
}
</style>
