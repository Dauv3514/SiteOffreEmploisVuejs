<script setup>
import Card from '@/components/Card.vue'
import { RouterLink } from 'vue-router';
</script>

<template>
     <!-- Developers and Employers -->
     <section class="py-4">
      <div class="container-xl lg:container m-auto">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 p-4 rounded-lg">
          <Card>
            <h2 class="text-2xl font-bold">Pour les développeurs</h2>
            <p class="mt-2 mb-4">
                Parcourez nos offres d'emploi Vue et démarrez votre carrière dès aujourd'hui
            </p>
            <RouterLink
              to="/jobs"
              class="inline-block bg-black text-white rounded-lg px-4 py-2 hover:bg-gray-700"
            >
              Parcourez les offres d'emplois.
            </RouterLink>
            </Card>
            <Card bg="bg-green-100">
                <h2 class="text-2xl font-bold">Pour les employeurs</h2>
                <p class="mt-2 mb-4">
                    Répertoriez votre travail pour trouver le développeur idéal pour le poste
                </p>
                <RouterLink
                    to="/jobs/ajouter"
                    class="inline-block bg-green-500 text-white rounded-lg px-4 py-2 hover:bg-green-600"
                    >
                    Ajouter un Job
                </RouterLink>
            </Card>
        </div>
      </div>
    </section>
</template>