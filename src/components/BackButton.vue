<script setup>
    import { RouterLink, useRoute } from 'vue-router';
</script>

<template>
    <!-- Go Back -->
    <section>
      <div class="bg-black container-xl m-auto py-6 px-6 border-0">
        <RouterLink
          to="/jobs"
          class="text-green-900 hover:text-green-900 flex items-center"
        >
          <i class="pi pi-arrow-circle-left mr-3"></i> Retour aux offres d'emplois
        </RouterLink>
      </div>
    </section>

</template>