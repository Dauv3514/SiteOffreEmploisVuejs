<script setup>
    import axios from 'axios';
    import { reactive, onMounted } from 'vue';
    import { RouterLink, useRoute, useRouter } from 'vue-router';
    import BackButton from '@/components/BackButton.vue';
    const route = useRoute();
    const router = useRouter();
    const jobId = route.params.id;
    const state = reactive({
        job: {},
    });

    const deleteJob = async() => {
        try {
            const confirm = window.confirm('Es tu sûr de vouloir supprimer ce job ?')
            if(confirm) {
                await axios.delete(`/api/jobs/${jobId}`);
                console.log('Job ID:', jobId);
                router.push('/jobs');
            }
        } catch(error) {
            console.error('Error Delinting job', error);
        }
    }

    onMounted(async () => {
        try {
            const response = await axios.get(`/api/jobs/${jobId}`);
            state.job = response.data;
        } catch (error) {
            console.error('Error fetching job', error);
        } 
    });
</script>

<template>
    <BackButton />
    <section v-if="state.job.company" class="bg-black px-4 py-[30.5px] pb-[160px] overflow-hidden">
      <div class="bg-black container m-auto py-10 px-6">
        <div class="grid grid-cols-1 md:grid-cols-70/30 w-full gap-6">
          <main>
            <div
              class="bg-white p-6 rounded-lg shadow-md text-center md:text-left"
            >
              <div class="text-gray-500 mb-4">{{ state.job.type }}</div>
              <h1 class="text-3xl font-bold mb-4">{{ state.job.title }}</h1>
              <div
                class="text-gray-500 mb-4 flex align-middle justify-center md:justify-start"
              >
                <i class="pi pi-map-marker text-xl text-orange-700 mr-2"></i>
                <p class="text-orange-700">{{ state.job.location }}</p>
              </div>
            </div>
  
            <div class="bg-white p-6 rounded-lg shadow-md mt-6">
              <h3 class="text-green-800 text-lg font-bold mb-6">
                Description du Job
              </h3>
  
              <p class="mb-4">
                {{ state.job.description }}
              </p>
  
              <h3 class="text-green-800 text-lg font-bold mb-2">Salaires</h3>
  
              <p class="mb-4">{{ state.job.salary }} / ans</p>
            </div>
          </main>
  
          <!-- Sidebar -->
          <aside>
            <!-- Company Info -->
            <div class="bg-white p-6 rounded-lg shadow-md">
              <h3 class="text-xl font-bold mb-6">Informations sur l'entreprise</h3>
  
              <h2 class="text-2xl">{{ state.job.company.name }}</h2>
  
              <p class="my-2">
                {{ state.job.company.description }}
              </p>
  
              <hr class="my-4" />
  
              <h3 class="text-xl">Contact Email:</h3>
  
              <p class="my-2 bg-green-100 p-2 font-bold">
                {{ state.job.company.contactEmail }}
              </p>
  
              <h3 class="text-xl">Contact Phone:</h3>
  
              <p class="my-2 bg-green-100 p-2 font-bold">
                {{ state.job.company.contactPhone }}
              </p>
            </div>
  
            <!-- Manage -->
            <div class="bg-white p-6 rounded-lg shadow-md mt-6">
              <h3 class="text-xl font-bold mb-6">Gérer l'offre</h3>
              <RouterLink
                :to="`/jobs/edit/${state.job.id}`"
                class="bg-green-700 hover:bg-green-600 text-white text-center font-bold py-2 px-4 rounded-full w-full focus:outline-none focus:shadow-outline mt-4 block"
                >Modifier le Job</RouterLink
              >
              <button
                @click="deleteJob"
                class="bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded-full w-full focus:outline-none focus:shadow-outline mt-4 block"
              >
                Supprimer le Job
              </button>
            </div>
          </aside>
        </div>
      </div>
    </section>
  </template>