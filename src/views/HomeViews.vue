<script setup>
  import Hero from '@/components/Hero.vue';
  import HomeCards from '@/components/HomeCards.vue';
  import JobListings from '@/components/JobListings.vue';
</script>

<template>
  <Hero 
    title="Devenez Développeur VueJS"
    subtitle="Trouvez l'emploi qui correspond à vos compétences et à vos besoins."
  />
  <HomeCards />
  <JobListings :limit="3" :showButton="true"/>
</template>