<script setup lang="ts">
interface EventActivity {
  text: string;
}

interface Event {
  title: string;
  subtitle: string;
  date: string;
  time: string;
  location: string;
  description: string;
  activities: EventActivity[];
  contact: string;
  instagram: string;
  bookingRequired: boolean;
  past: boolean;
}

const events: Event[] = [
  {
    title: '"Su in Malga"',
    subtitle: 'Piccoli Grandi Chef · Malga Biancoia',
    date: '2025-07-05',
    time: 'dalle 09:30 alle 12:00',
    location: 'Via Biancoia 1, Lusiana Conco (VI)',
    description: "Un'esperienza unica tra natura, tradizione e gusto!",
    activities: [
      { text: 'Visita alla malga e incontro con la vita del malghese' },
      { text: 'Scopri le fasi della lavorazione del latte' },
      { text: 'Laboratorio creativo per grandi e piccini: realizza una merenda con la ricotta fatta sul momento!' },
    ],
    contact: '347 109 4928 – Silvia',
    instagram: '@agriturismo_malga_biancoia',
    bookingRequired: true,
    past: true,
  }
];

const formatDate = (dateStr: string) => {
  return new Date(dateStr).toLocaleDateString('it-IT', {
    weekday: 'long',
    day: 'numeric',
    month: 'long',
    year: 'numeric',
  });
};
</script>

<template>
  <section id="events" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-bold text-center text-gray-900 mb-2">Eventi</h2>
      <p class="text-center text-gray-500 text-sm mb-12">Esperienze da vivere alla malga</p>

      <div class="space-y-8 max-w-2xl mx-auto">
        <article
          v-for="event in events"
          :key="event.title"
          class="bg-farm-50 rounded-xl overflow-hidden border border-farm-100"
          :class="{ 'opacity-75': event.past }"
        >
          <!-- Header -->
          <div class="bg-farm-600 px-6 py-5 text-white relative">
            <span
              v-if="event.past"
              class="absolute top-4 right-4 text-xs uppercase tracking-widest bg-white/20 text-white px-3 py-1 rounded-full"
            >Edizione passata</span>
            <h3 class="text-2xl font-bold font-serif italic">{{ event.title }}</h3>
            <p class="text-farm-100 text-sm font-semibold uppercase tracking-wider mt-1">{{ event.subtitle }}</p>
          </div>

          <!-- Body -->
          <div class="px-6 py-6 space-y-5">
            <!-- Info -->
            <div class="space-y-2 text-sm text-gray-700">
              <p class="flex items-center gap-2">
                <span class="text-farm-600">📍</span>
                {{ event.location }}
              </p>
              <p class="flex items-center gap-2">
                <span class="text-farm-600">📅</span>
                {{ formatDate(event.date) }}
              </p>
              <p class="flex items-center gap-2">
                <span class="text-farm-600">🕐</span>
                {{ event.time }}
              </p>
            </div>

            <p class="text-gray-600 italic text-sm">{{ event.description }}</p>

            <!-- Activities -->
            <div>
              <p class="text-sm font-semibold text-gray-800 mb-2">Cosa ti aspetta:</p>
              <ul class="space-y-2">
                <li
                  v-for="activity in event.activities"
                  :key="activity.text"
                  class="flex items-start gap-2 text-sm text-gray-700"
                >
                  <span class="text-farm-500 mt-0.5 flex-shrink-0">✦</span>
                  {{ activity.text }}
                </li>
              </ul>
            </div>

            <!-- Booking -->
            <div
              v-if="event.bookingRequired"
              class="border border-farm-300 bg-farm-100 rounded-lg px-4 py-3 text-sm text-farm-800 font-semibold text-center tracking-wide uppercase"
            >
              Evento su prenotazione
            </div>

            <!-- Contact -->
            <div class="text-sm text-gray-500 space-y-1">
              <p>📞 {{ event.contact }}</p>
              <p>📸 {{ event.instagram }}</p>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>
