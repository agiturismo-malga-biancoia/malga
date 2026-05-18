<script setup lang="ts">
const currentYear = new Date().getFullYear();

const links = {
  social: [
    { name: 'Instagram', href: 'https://www.instagram.com/agriturismo_malga_biancoia/' }
  ],
  contact: {
    phone: '+39 347 1094928',
    phone2: '+39 349 1482936',
    email: 'larivierasoc.agr@gmail.com'
  },
  position: { address: 'Via Biancoia, 1 – 36062 Lusiana Conco (VI)' }
};

const mapsUrl = 'https://www.google.com/maps/search/?api=1&query=Via+Biancoia+1+Lusiana+Conco+VI';
</script>

<template>
  <footer class="bg-farm-700 text-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10">
      <div class="grid grid-cols-1 sm:grid-cols-3 gap-8 text-center sm:text-left">

        <!-- Contatti -->
        <div>
          <h3 class="text-base font-semibold uppercase tracking-widest text-farm-200 mb-4">Contattaci</h3>
          <div class="space-y-2 text-farm-100 text-sm">
            <p>
              <a :href="`tel:${links.contact.phone.replace(/\s/g,'')}`" class="hover:text-white transition-colors">
                {{ links.contact.phone }}
              </a>
            </p>
            <p>
              <a :href="`tel:${links.contact.phone2.replace(/\s/g,'')}`" class="hover:text-white transition-colors">
                {{ links.contact.phone2 }}
              </a>
            </p>
            <p>
              <a :href="`mailto:${links.contact.email}`" class="hover:text-white transition-colors">
                {{ links.contact.email }}
              </a>
            </p>
          </div>
        </div>

        <!-- Posizione -->
        <div>
          <h3 class="text-base font-semibold uppercase tracking-widest text-farm-200 mb-4">Dove siamo</h3>
          <div class="space-y-3 text-farm-100 text-sm">
            <p>{{ links.position.address }}</p>
            <a
              :href="mapsUrl"
              target="_blank"
              rel="noopener noreferrer"
              class="inline-block mt-1 border border-farm-400 hover:border-white text-farm-200 hover:text-white text-xs uppercase tracking-wider px-4 py-2 rounded-sm transition-colors"
            >
              Apri in Google Maps
            </a>
          </div>
        </div>

        <!-- Social -->
        <div>
          <h3 class="text-base font-semibold uppercase tracking-widest text-farm-200 mb-4">Seguici</h3>
          <div class="space-y-2">
            <a
              v-for="social in links.social"
              :key="social.name"
              :href="social.href"
              class="inline-flex items-center gap-2 text-farm-100 hover:text-white transition-colors text-sm"
              target="_blank"
              rel="noopener noreferrer"
            >
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                <path d="M12 2.163c3.204 0 3.584.012 4.85.07 1.366.062 2.633.334 3.608 1.308.975.975 1.246 2.242 1.308 3.608.058 1.266.07 1.646.07 4.85s-.012 3.584-.07 4.85c-.062 1.366-.334 2.633-1.308 3.608-.975.975-2.242 1.246-3.608 1.308-1.266.058-1.646.07-4.85.07s-3.584-.012-4.85-.07c-1.366-.062-2.633-.334-3.608-1.308-.975-.975-1.246-2.242-1.308-3.608C2.175 15.584 2.163 15.204 2.163 12s.012-3.584.07-4.85c.062-1.366.334-2.633 1.308-3.608.975-.975 2.242-1.246 3.608-1.308C8.416 2.175 8.796 2.163 12 2.163zm0-2.163C8.741 0 8.332.014 7.052.072 5.197.157 3.355.673 2.014 2.014.673 3.355.157 5.197.072 7.052.014 8.332 0 8.741 0 12c0 3.259.014 3.668.072 4.948.085 1.855.601 3.697 1.942 5.038 1.341 1.341 3.183 1.857 5.038 1.942C8.332 23.986 8.741 24 12 24s3.668-.014 4.948-.072c1.855-.085 3.697-.601 5.038-1.942 1.341-1.341 1.857-3.183 1.942-5.038.058-1.28.072-1.689.072-4.948s-.014-3.668-.072-4.948c-.085-1.855-.601-3.697-1.942-5.038C20.645.673 18.803.157 16.948.072 15.668.014 15.259 0 12 0z"/>
                <path d="M12 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zm0 10.162a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"/>
              </svg>
              {{ social.name }}
            </a>
          </div>
        </div>
      </div>

      <!-- Copyright -->
      <div class="mt-10 pt-6 border-t border-farm-600 text-center text-farm-300 text-xs">
        <p>&copy; {{ currentYear }} Agriturismo Malga Biancoia · Tutti i diritti riservati</p>
      </div>
    </div>
  </footer>
</template>
