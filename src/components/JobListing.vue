<script setup>
import { defineProps, ref, computed } from 'vue';
import { RouterLink } from 'vue-router';

const props = defineProps({
    job: Object
});

const showFullDescription = ref(false);
const truncatedDescription = computed(() => {
    let description = props.job.description;
    if(!showFullDescription.value) {
        description = description.substring(0, 90) + '...';
    }
    return description;
});

const toogleFullDescription = () => {
    showFullDescription.value = !showFullDescription.value;
}
</script>

<template>
    <div class="ring ring-green-900 ring-1 rounded-xl shadow-md relative">
        <div class="p-4">
        <div class="mb-6">
            <div class="text-white my-2"> {{ job.type }}</div>
            <h3 class="text-white font-bold">{{ job.title }}</h3>
        </div>

        <div class="mb-5 text-white">
            <div>
                {{ truncatedDescription }}
            </div>
            <div 
                @click="toogleFullDescription"
                class="text-green-700 hover:text-green-800 mb-5">
                {{ showFullDescription ? 'Moins' : 'Plus' }}
            </div>
        </div>

        <h3 class="text-green-700 mb-2"> {{ job.salary }} / ans</h3>

        <div class="ring ring-white ring-1 mb-5"></div>

        <div class="flex flex-col lg:flex-row justify-between mb-4">
            <div class="text-orange-700 mb-3">
            <i class="pi pi-map-marker text-orange-700"></i>
                {{ job.location }}
            </div>
            <RouterLink
                :to="'/jobs/' + job.id"
                class="h-[36px] bg-green-700 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-center text-sm"
                >
                Voir plus
            </RouterLink>
        </div>
        </div>
    </div>
</template>