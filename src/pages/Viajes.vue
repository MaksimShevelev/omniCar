<template>
      <div class="absolute inset-0 -z-10 transform-gpu blur-3xl opacity-20" aria-hidden="true">
            <div class="aspect-[1097/845] w-full h-full bg-gradient-to-tr from-[#239e61] to-[#1d7e4b]"
                style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)"
            ></div>
        </div>
  <BaseHeading1 class="flex flex-col rounded-x justify-center text-3xl items-center text-center mt-4">Lista de viajes
  </BaseHeading1>
  <div class="flex bg-gray-100 rounded-xl gap-4 mb-40">

    <section class="w-full">
      <div class="p-4 border rounded">
        <BaseLoader v-if="loadingTrips" />

        <ul class="flex flex-col gap-4">
          <li v-for="trip in sortedTrips" :key="trip.id">
            <div class="bg-white p-4 border rounded-xl shadow-md">
              <div class="flex items-center justify-between text-xl">
                <div class="mb-1 flex items-center space-x-4">
                  <img
                    :src="trip.photoURL || 'path/to/default-photo.jpg'" 
                    alt="Фото профиля"
                    class="w-20 h-20 rounded-full border-2 border-gray-300 object-cover"
                  />
                  <div>
                    <h1 class="inline-flex items-center text-3xl space-x-2">
                      <b>{{ trip.displayName || 'Имя отсутствует' }}</b>
                    </h1>
                  </div>
                </div>
                <div class="mb-1 flex items-center space-x-2">
                  <span class="inline-block bg-gray-200 text-3xl my-4 p-4 border rounded-xl shadow text-gray-700 font-semibold">
                    {{ trip.price }} $ ARS
                  </span>
                </div>
            
              </div>

              <div class="text-2xl text-green-700">
                <h2 class="inline-flex items-center text-2xl text-green-700 my-4 px-4 py-2 border rounded-xl shadow">
                  <!-- Иконка для Origen -->
                  <span class="mr-2">
                    <svg width="38" height="38" viewBox="0 0 38 38" fill="none" xmlns="http://www.w3.org/2000/svg"
                      xmlns:xlink="http://www.w3.org/1999/xlink">
                      <rect width="38" height="38" fill="url(#pattern0_229_9574)" />
                      <defs>
                        <pattern id="pattern0_229_9574" patternContentUnits="objectBoundingBox" width="1" height="1">
                          <use xlink:href="#image0_229_9574" transform="scale(0.02)" />
                        </pattern>
                        <image id="image0_229_9574" width="50" height="50"
                          xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAACUklEQVR4nO2ZS2sUQRCAP19EySoiEZUEAkFBiOCe4uYHeBO9RXPKWfAUBQ8eJCEs3kQ95PULPMSDt+BF8R1EL4K5JkhQE8FgFNfXSEMFliUmXdnqnh7xg4JlZqiaj+6p2emG/6zJbqAfmABmgA/Adwn3+7mcOyfXJschYBT4AmSe4a6dBA6TAC3AMLCiEGgMN1rXJFcutAEPmhBojCfAwdgSx4B5Q4nVmJPcUTgQSKJextUIyk6ZAlngeBz6mRmOIJFJVEO22Ga6kzZqQFcIkdGIEpnEuLVECficg8iK1DajX3kD34AbwAmgVcL9vinnNLn6LEUmFIXfAsfXyVWWa3zzjVmKzChGYj2JehnfkXlmKbLoWdRNJ19ueeZ8bylS8yzao8hZUYyyGb7TQNNhSp45v9ppwLsAIns8cy5YirzJcWq9thS561nUvSesH/YpS5Gq4sF0rXUjyooGMmQp0udZNJOXXdnwhXjaUmQ/8EtRvCZTpyINwEWvHPMdiQz4IU3BlFeKG7CKhxT8oyqTuBRC5Ghkid9AJ4F4GVHkPgE5H1HkbEgR130+RZBYAHYQmOsRRK4QgY5NfK5qYhnYSyTGAoqMEJH2QGtcH4F9RGYogMgFcmCX8WL2bIxO9TcGDEVOkSNbgRcGEvdIgLJsn21Wwu0lHiERqk2IDJIQLbJIoJVw29XbSIwK8FMh4f4ddJMoIwqRiyTMduCRh8S0dLyk6QCWNliUdtt4heCMfKo2Srhn6CQF4+oaIpcpIFuA23USd+RYISnJjtNT601N/lX+AJW6sAqkjpn4AAAAAElFTkSuQmCC" />
                      </defs>
                    </svg>

                  </span>
                  <!-- Текст для Origen -->
                  <strong class="text-gray-900">Origen -  <span class="text-green-700"> {{ trip.origin || 'Не указан' }} </span></strong>
                </h2>
              </div>

              <div class="text-2xl text-green-700">
                <h2 class="inline-flex items-center text-2xl text-green-700 my-4 px-4 py-2 border rounded-xl shadow">
                  <!-- Иконка для Destino -->
                  <span class="mr-2">
<svg width="38" height="50" viewBox="0 0 38 50" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
<rect width="38" height="50" fill="url(#pattern0_241_9573)"/>
<defs>
<pattern id="pattern0_241_9573" patternContentUnits="objectBoundingBox" width="1" height="1">
<use xlink:href="#image0_241_9573" transform="matrix(0.02 0 0 0.0152 0 0.12)"/>
</pattern>
<image id="image0_241_9573" width="50" height="50" xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAADN0lEQVR4nO2ZS2gTURSGry+q+EBEUbGY5t6JShUVBB8rV+5EV/WB0jknkYJiNyq4cBGUUtxJqqDJnNuIrizowp24UXy1IroRdKtIsVVBsRVbq5WTqG1pU++kdyYT8YcDYTKcO9+cx32MEP81XqspOV9q3C815hThY0nQKzUMFoygV2no4v8kufv4XhE1rcw2LVcaLioN/UrjsJlBvyT0lJdyKv38wsk01yiCM5KwzxxgrHG0lMaz7EtUQquyTYulhrvlAkwA9DCWd5eFCiEpuU4SvrYFMcpese9QIOJeamlAEH9geIxAIWJ5dzanQIAQw4U0I3wQaM1wYQcNoUZgWgNrsVPpTmWADCQ0SusgxXkiHAj12wiyViHqLxyZJzV8DhtEEvbx2NZAeNnh6wE0fFUEmYTGLeuvHJzLxr+lxrbCf/6A9tgEyfl4i2/qNG4o5SuRdzfyPT5ALlkD4QWgaSQmgxgDYxgZSdBpDURqeGdYnBlzn3jezCf22AMhHDAZNO6lNpv6dHLuVtMoC2sghmngp8PwvYYR+WINRGl4axvEuXpggVmxQ7c9EMIXlUstfG4NRGq8aThom/Vi13jdHghhq2lhcmv9m79fc4lRA1EEp62B8OzqZ0KcDMb3hEjJXdZAHI1LlIbvPmAGOHW4DrgBFDoUJbfxNeNI6EKEv3FTEDYlCZ8Zv0VbRnBPVPOmSo2AnLAOEsu7a8KFwB91lIyJICQ1PA0LRBLcCQSiCIKHQ4tIO+wNDKS4PoKPwYNA96Zs0ywRpBTBuRAickoELSd3qLaM7aqP2sBPsby7UIQh3n4GWOQtIiwlLjeuCOaMCz7UeqlFIkzxYs46iAdHRdiq7WiYY/cwG14G3qlKSXrg2gKJa9wpKqZ0errS+GTKIAS3RaWVKJ5RDU4hpfplOyREFCQNd5AlonFMREVOprmGDwnKiEaX6GiYIaIkh09FCIdMIQqrg1zjWhFFSYIWHxE5LqKq7en0TKXxvkE0bnHHE1GWw4tKwvelixt7+DOeqAapdtjNW9UJIIbiHuwQ1SRJkB6XUgQnRdVpWEyTBNdGzRc3+JqoRtXzR1SCTqnxkdWPmuIf1k9gLEjA0NwZhgAAAABJRU5ErkJggg=="/>
</defs>
</svg>




                  </span>
                  <!-- Текст для Destino -->
                  <strong class="text-gray-900">Destino - <span class="text-green-700">   {{ trip.destination || 'Не указано' }} </span></strong>
                </h2>

                <div class="flex items-center gap-2 mt-2 mb-4">
                  <div class="inline-flex items-center text-2xl text-green-700 px-4 py-2 border rounded-xl shadow">
                  <!-- Иконка для даты и времени -->
                  <span class="mr-2">
                    <svg width="38" height="38" viewBox="0 0 38 38" fill="none" xmlns="http://www.w3.org/2000/svg"
                      xmlns:xlink="http://www.w3.org/1999/xlink">
                      <rect width="38" height="38" fill="url(#pattern0_230_9576)" />
                      <defs>
                        <pattern id="pattern0_230_9576" patternContentUnits="objectBoundingBox" width="1" height="1">
                          <use xlink:href="#image0_230_9576" transform="scale(0.02)" />
                        </pattern>
                        <image id="image0_230_9576" width="50" height="50"
                          xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAAByklEQVR4nO2ZPUvDUBSGn8HFwaGICkVExE3EoYMIIh26OomI6HAnVwcdozjW4h/oFCf/QNXFobg4OepY3NRFBBc/lkrwFg6hxZs2aW7a+8K7PJCevBzObXICTk6pqgI0tPczXAMfaGqfZLgGmQ0yr1t9DdwAz6JIQ7O43a7GpQ411U2IbeBL/KgNfgeKUUIsAT8W3HizQxjjzpyLC1+AA2APuBO8plncblfDAz4EPzYN8iAu2rFk2D3Bg5kx0pO4qGhJECV4vdcgm0BZuxTv/f9bQ8UZJE0pF4S/jpwldDpFtd9rR2x0faiD3Cf0TBXVj27YGcLjdwyY084LPiJ4YKkZwUcFnxA81+8gnYrMhobUpEZfHlFcEDLSkX5IuSAMcEcqHZZnG4JfCD4teGCpW8GXDWqoOINEHURrj19/UIIs6NfPUuifOi94QfBRwcOvxquC5wxqKHdqMcCnlgKq2uuCrwgeLPNaGhe8alMQP8Zhd0FIcEFXEDzYeLSUE7xsU0fSlOomiFxi72KHvNCW3khyqF+Bw5SXc17os8KRaZBF4DuhnVSvfgMmo7RyC/i0MMQaXSh41jkFrlJeztX0V6pInXBycnLCev0CyQy2aCV3ZFcAAAAASUVORK5CYII=" />
                      </defs>
                    </svg>
                  </span>
                  <!-- Текст для даты и времени -->
                  {{ trip.date || 'Не указана' }} - {{ trip.time || 'Не указано' }}
                </div>

              </div>

              </div>
              


              <div class="flex items-center justify-between my-4">
                <!-- Контейнер для даты и времени -->
                <span v-for="option in trip.options" :key="option.icon" v-html="option.icon"
                class="inline-block p-2"></span>

                <!-- Кнопка "Reservar" справа -->
                <button @click="openModal(trip)"
                  class="ml-auto py-3 px-6 text-lg font-semibold rounded bg-green-700 text-white transition-all focus:bg-green-500 hover:bg-green-500 active:bg-green-900">
                  Ver más
                </button>

              </div>

            </div>

          </li>
        </ul>
      </div>
    </section>
  </div>

  <!-- Modal for Reservar -->
  <TransitionRoot as="div" :show="modalOpen">
  <Dialog class="relative mt-20 mb-20 z-40" @close="closeModal">
    <TransitionChild as="div" enter="ease-out duration-300" enter-from="opacity-0" enter-to="opacity-100"
      leave="ease-in duration-200" leave-from="opacity-100" leave-to="opacity-0">
      <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />
    </TransitionChild>

    <div class="fixed inset-0 z-10 w-screen overflow-y-auto">
      <div class="flex min-h-full items-stretch justify-center text-center">
        <TransitionChild as="div" enter="ease-out duration-300"
          enter-from="opacity-0 translate-y-4 md:translate-y-0 md:scale-95"
          enter-to="opacity-100 translate-y-0 md:scale-100" leave="ease-in duration-200"
          leave-from="opacity-100 translate-y-0 md:scale-100"
          leave-to="opacity-0 translate-y-4 md:translate-y-0 md:scale-95">
          
          <!-- Full-width DialogPanel -->
          <DialogPanel class="flex w-full transform text-left text-base transition bg-white rounded shadow-lg p-0">
            
            <!-- Close Button -->
            <button type="button" class="absolute right-4 top-4 text-gray-400 hover:text-gray-500"
              @click="closeModal">
              <span class="sr-only">Close</span>
              <XMarkIcon class="h-6 w-6" aria-hidden="true" />
            </button>

            <!-- Modal Content -->
            <div v-if="selectedTrip" class="w-full p-6">
              <h2 class="text-3xl font-bold">Viaje de {{ selectedTrip.displayName || 'Información de viaje' }}</h2>
              <h3 class="inline-flex text-xl my-2 p-4 border rounded-xl shadow text-green-700">
                <strong>Precio x asiento: <span class="text-gray-900"> {{ selectedTrip.price }} </span> $ ARS</strong> 
              
              </h3>
              <!-- Trip Details -->
              <div class="my-4 text-lg">
              
              <h3 class="inline-flex text-xl my-2 p-4 border rounded-xl shadow text-green-700">
              <strong>Cantidad de asientos: <span class="text-gray-900"> {{ selectedTrip.numSeats || 'Не указано' }} </span></strong>
              </h3>
                <p><strong>Origen:</strong> {{ selectedTrip.origin || 'Не указан' }}</p>
                <p><strong>Destino:</strong> {{ selectedTrip.destination || 'Не указано' }}</p>
                <p><strong>Fecha:</strong> {{ selectedTrip.date || 'Не указана' }}</p>
                <p><strong>Horario de salida:</strong> {{ selectedTrip.time || 'Не указано' }}</p>
              </div>

              <!-- Map Image -->
              <div v-if="selectedTrip.mapSnapshot">
                <img :src="selectedTrip.mapSnapshot" alt="Mapa de la ruta" class="rounded mt-4 w-full h-auto" />
              </div>

              <!-- Options Section -->
              <div class="my-4">
                <h3 class="block mb-2 text-xl text-green-700">Opciones</h3>
                <div v-if="selectedTrip.options && selectedTrip.options.length" class="grid grid-cols-2 gap-2">
                  <span v-for="option in selectedTrip.options" :key="option.name" class="flex items-center">
                    <span v-html="option.icon" class="mr-2"></span>
                    <span>{{ option.name }}</span>
                  </span>
                </div>
                <div v-else>
                  <p>Опции не указаны</p>
                </div>
              </div>
    <!-- Другие детали поездки -->
    
    <!-- Блок с описанием -->
     <!-- Проверка наличия описания перед выводом -->


    <p><strong>Descripción:</strong> {{ selectedTrip.description || 'Описание отсутствует' }}</p>

              <!-- Comments Section -->
              <div class="bg-gray-200 mb-10 p-4 rounded mt-4 w-full">
                <h3 class="text-lg mt-2">Preguntas</h3>
                <ul class="ml-4">
                  <li v-for="comment in comments[selectedTrip.id]" :key="comment.id">
                    <b>{{ comment.rol }}</b> - <b>{{ comment.displayName }}:</b> {{ comment.text }}
                  </li>
                </ul>
                <form @submit.prevent="handleCommentSubmit(selectedTrip.id)" class="mt-2">
                  <textarea v-model="newComment[selectedTrip.id]" class="w-full min-h-8 p-2 border rounded"></textarea>
                  <button type="submit"
                    class="mt-2 py-2 px-4 rounded bg-green-700 text-white transition-all focus:bg-green-500 hover:bg-green-500 active:bg-green-900">
                    Enviar
                  </button>
                </form>
              </div>

              

              <!-- Confirm Button -->
              <router-link
                :to="`/usuario/${selectedTrip.user_id}`"
                class="mt-4 px-4 py-2 bg-green-600 text-white rounded text-lg font-semibold transition-all focus:bg-green-500 hover:bg-green-500 active:bg-green-900"
              >
                Reservar
              </router-link>
            </div>

          </DialogPanel>
        </TransitionChild>
      </div>
    </div>
  </Dialog>
</TransitionRoot>



</template>







<script>
import BaseHeading1 from '../components/BaseHeading1.vue';
import BaseLoader from '../components/BaseLoader.vue';
import ProfileData from '../components/profile/ProfileData.vue';
import { subscribeToAuthState } from '../services/auth.js';
import { subscribeToTrips, saveChatMessage, subscribeToChatMessages, saveComment, subscribeToComments } from '../services/viajes.js';
import { getUserProfileById } from '../services/user-profile.js';
import { ref } from 'vue';
import { Dialog, DialogPanel, TransitionChild, TransitionRoot } from '@headlessui/vue';
import { XMarkIcon } from '@heroicons/vue/24/outline';

export default {
  name: 'Viajes',
  components: {
    BaseHeading1, BaseLoader, ProfileData, Dialog, DialogPanel, TransitionChild, TransitionRoot, XMarkIcon
  },
  data() {
    return {
      loadingTrips: false,
      trips: [],
      comments: {},
      newComment: {},
      loggedUser: {
        id: null,
        email: null,
        displayName: null,
        rol: null,
        bio: null,
      },
      unsubscribeChat: null,
      modalOpen: false,
      confirmModalOpen: false, // Controls the confirmation modal
      selectedTrip: null,
      selectedTrip: null,
    };
  },
  methods: {
    async loadUserProfile(trip) {
      const profile = await getUserProfileById(trip.user_id);
      if (profile) {
        trip.email = profile.email;
        trip.displayName = profile.displayName;
        trip.rol = profile.rol;
        trip.photoURL = profile.photoURL || 'path/to/default-photo.jpg';
      } else {
        trip.email = 'Неизвестный пользователь';
        trip.displayName = 'Имя отсутствует';
        trip.rol = 'без роли';
        trip.photoURL = 'path/to/default-photo.jpg';
      }
    },
    async handleCommentSubmit(tripId) {
      if (!this.newComment[tripId]?.trim()) {
        console.error("El texto del comentario está vacío");
        return;
      }
      await saveComment({
        viajeId: tripId,
        user_id: this.loggedUser.id,
        text: this.newComment[tripId],
        displayName: this.loggedUser.displayName || 'Anónimo',
        rol: this.loggedUser.rol,
      });
      this.newComment[tripId] = '';
      this.fetchComments(tripId);
    },
    fetchComments(tripId) {
      subscribeToComments(tripId, (comments) => {
        this.comments[tripId] = comments;
      });
    },
    formatDate(date) {
      if (!date) return null;
      const formatter = new Intl.DateTimeFormat('es-AR', {
        day: '2-digit', month: '2-digit', year: 'numeric',
        hour: '2-digit', minute: '2-digit', hour12: false
      });
      return formatter.format(date).replace(',', '');
    },
    
    openModal(trip) {
    this.selectedTrip = null; // сброс
    this.$nextTick(() => {
        this.selectedTrip = trip;
        this.modalOpen = true;
        this.fetchComments(trip.id);
    });
},

  closeModal() {
    this.modalOpen = false;
    this.selectedTrip = null;
    this.comments = {};
  },
    openConfirmationModal() {
      this.confirmModalOpen = true;
    },
    closeConfirmationModal() {
      this.confirmModalOpen = false;
    },
    async reserveTrip(tripId) {
      console.log(`Trip ${tripId} reserved`);
      this.closeModal();
      this.openConfirmationModal();
    }
  },
  async mounted() {
    this.loadingTrips = true;
    this.unsubscribeChat = subscribeToChatMessages(async (newMessages) => {
      this.loadingTrips = false;
      for (const message of newMessages) {
        await this.loadUserProfile(message);
      }
      this.trips = newMessages;
    });

    this.unsubscribeAuth = subscribeToAuthState(newUserData => this.loggedUser = newUserData);

    subscribeToTrips((fetchedTrips) => {
    this.trips = fetchedTrips.map(trip => ({
        ...trip,
        description: trip.description || 'Описание отсутствует', // Убедитесь, что description присутствует
    }));
});
  },
  unmounted() {
    if (this.unsubscribeAuth) this.unsubscribeAuth();
    if (typeof this.unsubscribeChat === 'function') this.unsubscribeChat();
  },
  computed: {
    sortedTrips() {
      return this.trips.slice().sort((a, b) => new Date(a.date) - new Date(b.date));
    }
  }
}
</script>