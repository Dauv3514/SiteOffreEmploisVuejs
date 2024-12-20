<script setup>
    import router from '@/router';
    import { reactive } from 'vue';
    import axios from 'axios';

    const form = reactive({
        type: 'Temps plein',
        title: '',
        description: '',
        salary: '',
        location: '',
        company: {
            name: '',
            description: '',
            contactEmail: '',
            contactPhone: '',
        }
    })

    const handleSubmit = async () => {
        const newJob = {
            type: form.type,
            title: form.title,
            description: form.description,
            salary: form.salary,
            location: form.location,
            company: {
                name: form.name,
                description: form.description,
                contactEmail: form.contactEmail,
                contactPhone: form.contactPhone,
            }
        }
        console.log(newJob, 'ok');

        try {
            const response = await axios.post('/api/jobs', newJob);
            router.push(`/jobs/${response.data.id}`);
            console.log('Job created:', response.data);
        } catch (error) {
            console.error('Error creating job:', error);
        }
    }
</script>

<template>
    <section class="bg-black">
      <div class="container m-auto max-w-2xl py-24">
        <div
          class="bg-white px-6 py-8 mb-4 shadow-md rounded-md border m-4 md:m-0"
        >
          <form @submit.prevent="handleSubmit">
            <h2 class="text-3xl text-center font-semibold mb-6">Ajouter un Job</h2>

            <div class="mb-4">
              <label for="type" class="block text-gray-700 font-bold mb-2"
                >Type</label
              >
              <select
                v-model="form.type"
                id="type"
                name="type"
                class="border rounded w-full py-2 px-3"
                required
              >
                <option value="Full-Time">Temps plein</option>
                <option value="Part-Time">Temps partiel</option>
                <option value="Remote">Remote</option>
                <option value="Internship">Stage</option>
              </select>
            </div>

            <div class="mb-4">
              <label class="block text-gray-700 font-bold mb-2"
                >Titre</label
              >
              <input
                type="text"
                v-model="form.title"
                id="name"
                name="name"
                class="border rounded w-full py-2 px-3 mb-2"
                placeholder="Intitulé du poste"
                required
              />
            </div>
            <div class="mb-4">
              <label
                for="description"
                class="block text-gray-700 font-bold mb-2"
                >Description</label
              >
              <textarea
                v-model="form.description"
                id="description"
                name="description"
                class="border rounded w-full py-2 px-3"
                rows="4"
                placeholder="Ajouter les fonctions, les attentes, les exigences etc."
              ></textarea>
            </div>

            <div class="mb-4">
              <label for="type" class="block text-gray-700 font-bold mb-2"
                >Salaire</label
              >
              <select
                id="salary"
                v-model="form.salary"
                name="salary"
                class="border rounded w-full py-2 px-3"
                required
              >
                <option value="Moins €45K">moins €45K</option>
                <option value="€45K - €55K">€45K - €55K</option>
                <option value="€55K - €65K">€55K - €65K</option>
                <option value="€65K - €75K">€65K - €75K</option>
                <option value="€75K - €85K">€75K - €85K</option>
                <option value="€85K - €95K">€85K - €95K</option>
                <option value="€95K - €115K">€95K - €115K</option>
                <option value="€115K - €140K">€115K - €140K</option>
                <option value="€140K - €165K">€140K - €165K</option>
                <option value="€165K - €185K">€165K - €185K</option>
                <option value="Plus €185K">Over €185K</option>
              </select>
            </div>

            <div class="mb-4">
              <label class="block text-gray-700 font-bold mb-2">
                Lieu
              </label>
              <input
                type="text"
                v-model="form.location"
                id="location"
                name="location"
                class="border rounded w-full py-2 px-3 mb-2"
                placeholder="Adresse de l'entreprise"
                required
              />
            </div>

            <h3 class="text-2xl mb-5">Informations sur l'entreprise</h3>

            <div class="mb-4">
              <label for="company" class="block text-gray-700 font-bold mb-2"
                >Nom</label
              >
              <input
                type="text"
                v-model="form.company.name"
                id="company"
                name="company"
                class="border rounded w-full py-2 px-3"
                placeholder="Nom de l'entreprise"
              />
            </div>

            <div class="mb-4">
              <label
                for="company_description"
                class="block text-gray-700 font-bold mb-2"
                >Description</label
              >
              <textarea
                id="company_description"
                v-model="form.company.description"
                name="company_description"
                class="border rounded w-full py-2 px-3"
                rows="4"
                placeholder="Que fait votre entreprise ?"
              ></textarea>
            </div>

            <div class="mb-4">
              <label
                for="contact_email"
                class="block text-gray-700 font-bold mb-2"
                >Email</label
              >
              <input
                type="email"
                v-model="form.company.contactEmail"
                id="contact_email"
                name="contact_email"
                class="border rounded w-full py-2 px-3"
                placeholder="Email pour les candidats"
                required
              />
            </div>
            <div class="mb-4">
              <label
                for="contact_phone"
                class="block text-gray-700 font-bold mb-2"
                >Téléphone</label
              >
              <input
                type="tel"
                v-model="form.company.contactPhone"
                id="contact_phone"
                name="contact_phone"
                class="border rounded w-full py-2 px-3"
                placeholder="Téléphone facultatif pour les candidats"
              />
            </div>

            <div>
              <button
                class="bg-green-900 hover:bg-green-600 text-white font-bold py-2 px-4 rounded-full w-full focus:outline-none focus:shadow-outline"
                type="submit"
              >
                Ajouter un Job
              </button>
            </div>
          </form>
        </div>
      </div>
    </section>
</template>