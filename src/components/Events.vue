<script setup lang="ts">
import event1 from '../images/events/event_1.webp';
import event2 from '../images/events/event_2.webp';
import event3 from '../images/events/event_3.webp';

const photos = [event1, event2, event3];
</script>

<template>
  <section id="events" class="py-20 bg-farm-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Titolo sezione -->
      <h2 class="text-3xl font-bold text-center text-gray-900 mb-2">Eventi</h2>
      <p class="text-center text-gray-500 text-sm mb-14">Esperienze da vivere alla malga</p>

      <!-- Card evento -->
      <div class="max-w-3xl mx-auto bg-white rounded-2xl shadow-sm border border-farm-100 overflow-hidden">

        <!-- Header verde -->
        <div class="bg-farm-600 px-8 py-6 text-white">
          <p class="text-xs uppercase tracking-widest text-farm-200 mb-1">Evento</p>
          <h3 class="text-3xl font-bold italic">"Su in Malga"</h3>
          <p class="text-farm-100 text-sm font-semibold uppercase tracking-wider mt-1">Piccoli Grandi Chef · Malga Biancoia</p>
        </div>

        <!-- Corpo -->
        <div class="px-8 py-8 space-y-8">

          <!-- Descrizione -->
          <p class="text-gray-600 text-base leading-relaxed italic border-l-4 border-farm-300 pl-4">
            Un'esperienza unica tra natura, tradizione e gusto: portiamo grandi e piccini a scoprire la vita autentica della malga, dal pascolo delle mucche alla magia della lavorazione del latte.
          </p>

          <!-- Cosa ti aspetta -->
          <div>
            <h4 class="text-sm font-semibold uppercase tracking-widest text-farm-700 mb-4">Cosa ti aspetta</h4>
            <ul class="space-y-3">
              <li class="flex items-start gap-3 text-gray-700">
                <span class="text-farm-500 mt-0.5 flex-shrink-0 font-bold">✦</span>
                <span><strong class="text-gray-900">Visita alla malga</strong> e incontro con la vita del malghese</span>
              </li>
              <li class="flex items-start gap-3 text-gray-700">
                <span class="text-farm-500 mt-0.5 flex-shrink-0 font-bold">✦</span>
                <span>Scopri le <strong class="text-gray-900">fasi della lavorazione del latte</strong></span>
              </li>
              <li class="flex items-start gap-3 text-gray-700">
                <span class="text-farm-500 mt-0.5 flex-shrink-0 font-bold">✦</span>
                <span><strong class="text-gray-900">Laboratorio creativo</strong> per grandi e piccini: realizza una merenda con la ricotta fatta sul momento!</span>
              </li>
            </ul>
          </div>

          <!-- Foto -->
          <div>
            <h4 class="text-sm font-semibold uppercase tracking-widest text-farm-700 mb-4">Le foto dell'evento</h4>
            <div class="grid grid-cols-1 sm:grid-cols-3 gap-3">
              <img
                v-for="(photo, index) in photos"
                :key="index"
                :src="photo"
                :alt="`Foto evento Su in Malga ${index + 1}`"
                class="w-full h-52 object-cover rounded-lg hover:scale-105 transition-transform duration-300 cursor-pointer"
              />
            </div>
          </div>

          <!-- Info prenotazione -->
          <div class="bg-farm-50 border border-farm-200 rounded-xl px-6 py-4 flex flex-col sm:flex-row sm:items-center sm:justify-between gap-3">
            <div>
              <p class="text-sm font-semibold text-farm-800 uppercase tracking-wide">Evento su prenotazione</p>
              <p class="text-xs text-gray-500 mt-0.5">Per info e prenotazioni contattaci</p>
            </div>
            <a
              href="tel:+393471094928"
              class="inline-block bg-farm-600 hover:bg-farm-500 text-white text-sm font-semibold px-5 py-2.5 rounded-lg transition-colors"
            >
              📞 347 109 4928 – Silvia
            </a>
          </div>

        </div>
      </div>

    </div>
  </section>
</template>
