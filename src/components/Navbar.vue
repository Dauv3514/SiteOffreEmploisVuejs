<script setup>
    import logo from '@/assets/img/logo.png'
    import { RouterLink, useRoute } from 'vue-router';

    const isActiveLink = (routePath) => {
        const router = useRoute();
        return router.path === routePath;
    }
</script>

<template>
    <nav class="bg-black border-b border-green-900">
      <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
        <div class="flex h-20 items-center justify-between">
          <div
            class="flex flex-1 items-center justify-center md:items-stretch md:justify-start"
          >
            <!-- Logo -->
            <RouterLink class="flex flex-shrink-0 items-center mr-4" to="/">
              <img class="h-10 w-auto" :src="logo" alt="Vue Jobs" />
              <span class="hidden md:block text-white text-2xl font-bold ml-2"
                >VueJS Jobs</span
              >
            </RouterLink>
            <div class="md:ml-auto">
              <div class="flex space-x-2">
                <RouterLink
                  to="/"
                  :class="[isActiveLink('/') ? 'bg-green-900' : 'hover:bg-green-900','text-white', 'px-3', 'py-2', 'rounded-md']"
                  >Home
                </RouterLink>
                <RouterLink
                  to="/jobs"
                  class="text-white hover:bg-green-900 hover:text-white rounded-md px-3 py-2"
                  >Jobs
                </RouterLink>
                <RouterLink
                  to="/jobs/add"
                  class="text-white hover:bg-green-900 hover:text-white rounded-md px-3 py-2"
                  >Ajouter un Job
                </RouterLink>
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
  </template>