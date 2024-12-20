<script setup>
    import { ref, defineProps, onMounted } from 'vue';
    import JobListing from './JobListing.vue';
    import axios from 'axios';

    defineProps({
        limit: Number,
        showButton: {
            type: Boolean,
            default: false
        }
    })
    const jobs = ref([]);
    onMounted(async () => {
        try {
            const response = await axios.get('api/jobs');
            jobs.value = response.data;
        } catch {

        }
    })
</script>

<template>
   <section class="bg-[#090a0a] 0 px-4 py-10">
    <div class="container-xl lg:container m-auto">
      <h2 class="text-3xl font-bold text-white mb-6 text-center">
        Parcourir les offres d'emplois
      </h2>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <JobListing v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id" :job="job">
            {{ job.title }}
        </JobListing>
    </div>
    <div v-if="showButton" class="bg-black 0 m-auto max-w-lg my-10 px-6">
        <a
        href="jobs"
        class="block bg-green-700 text-white text-center py-4 px-6 rounded-xl hover:bg-green-900"
        >Voir tous les jobs</a
      >
    </div>
  </section>

</template>