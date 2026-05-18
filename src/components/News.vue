<script setup lang="ts">
import { TrophyIcon } from '@heroicons/vue/24/outline';

interface NewsItem {
  title: string;
  date: string;
  awards: string[];
}

const news: NewsItem[] = [
  {
    title: 'CASEUS 2025',
    date: '2025-10-05',
    awards: [
      '1° Classificato Allevo Biancoia',
      '1° Classificato Caciotta di Malga'
    ]
  },
  {
    title: 'CASEUS 2024',
    date: '2024-10-05',
    awards: ['1° Classificato Formaggio di Fattoria Caciotta']
  },
  {
    title: 'SU IN MALGA! - Gallio',
    date: '2024-07-28',
    awards: ['2° Classificato Nostrano Biancoia']
  }
];
</script>

<template>
  <section id="news" class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-bold text-center text-gray-900 mb-12">News</h2>
      <div class="space-y-8">
        <article v-for="item in news" :key="item.title"
                 class="bg-white p-6 rounded-lg shadow-md">
          <div class="flex justify-between items-start mb-4">
            <h3 class="text-xl font-semibold text-gray-900">{{ item.title }}</h3>
            <time :datetime="item.date" class="text-sm text-gray-500">
              {{ new Date(item.date).toLocaleDateString('it-IT') }}
            </time>
          </div>
          <ul class="space-y-2">
            <li v-for="award in item.awards" :key="award"
                class="text-gray-600 flex items-center space-x-2">
              <TrophyIcon class="w-5 h-5 text-farm-600 flex-shrink-0" />
              <span>{{ award }}</span>
            </li>
          </ul>
        </article>
      </div>
    </div>
  </section>
</template>
