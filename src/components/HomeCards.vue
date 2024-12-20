<script setup>
import Card from '@/components/Card.vue'
import { RouterLink } from 'vue-router';
</script>

<template>
     <!-- Developers and Employers -->
      <div class="container-xl m-auto bg-black border border-black">
        <div class="grid grid-cols-1 md:grid-cols-2 w-3/4 mx-auto gap-4 p-2 rounded-lg">
          <Card>
            <h2 class="text-2xl font-bold text-white">Pour les développeurs</h2>
            <p class="mt-2 mb-4 text-white">
                Parcourez nos offres d'emplois et démarrez votre carrière dès aujourd'hui
            </p>
            <RouterLink
              to="/jobs"
              class="inline-block bg-[#e5f9e9] text-black rounded-lg px-4 py-2 hover:bg-gray-100"
            >
              Parcourez les offres d'emplois
            </RouterLink>
            </Card>
            <Card bg="bg-[#e5f9e9]">
                <h2 class="text-2xl font-bold">Pour les employeurs</h2>
                <p class="mt-2 mb-4">
                  Publiez votre offre d'emploi pour attirer le développeur idéal pour le poste
                </p>
                <RouterLink
                    to="/jobs/add"
                    class="inline-block bg-green-700 text-white rounded-lg px-4 py-2 hover:bg-green-600"
                >
                    Ajouter un Job
                </RouterLink>
            </Card>
        </div>
      </div>
</template>