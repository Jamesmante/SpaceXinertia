<template>
    <div>
      <h1 class="text-3xl font-semibold mb-6">Astronaut Applications</h1>
      <Link href="{{ route('recruitment.create') }}" class="bg-blue-500 text-white px-4 py-2 rounded mb-6 inline-block">Apply Now</Link>
      <ul>
        <li v-for="application in applications" :key="application.id" class="mb-4">
          <h2 class="text-2xl">{{ application.name }}</h2>
          <p>{{ application.email }}</p>
          <p>{{ application.phone }}</p>
          <p>{{ application.experience }}</p>
          <Link :href="route('recruitment.show', application.id)" class="text-blue-500">View</Link>
          <Link :href="route('recruitment.edit', application.id)" class="text-yellow-500">Edit</Link>
          <form :action="route('recruitment.destroy', application.id)" method="POST" @submit.prevent="destroy(application.id)">
            @csrf
            @method('DELETE')
            <button type="submit" class="text-red-500">Delete</button>
          </form>
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { Link, useForm } from '@inertiajs/vue3';
  
  const props = defineProps({
    applications: Array
  });
  
  const { delete: destroy } = useForm();
  </script>
  