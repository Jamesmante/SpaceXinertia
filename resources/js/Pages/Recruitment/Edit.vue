<template>
    <div>
      <h1 class="text-3xl font-semibold mb-6">Edit Application</h1>
      <form @submit.prevent="submit">
        <div>
          <label for="name" class="block text-sm font-medium">Name</label>
          <input v-model="form.name" type="text" id="name" class="block w-full mt-1" />
          <span v-if="form.errors.name" class="text-red-500 text-sm">{{ form.errors.name }}</span>
        </div>
        <div class="mt-4">
          <label for="email" class="block text-sm font-medium">Email</label>
          <input v-model="form.email" type="email" id="email" class="block w-full mt-1" />
          <span v-if="form.errors.email" class="text-red-500 text-sm">{{ form.errors.email }}</span>
        </div>
        <div class="mt-4">
          <label for="phone" class="block text-sm font-medium">Phone</label>
          <input v-model="form.phone" type="text" id="phone" class="block w-full mt-1" />
          <span v-if="form.errors.phone" class="text-red-500 text-sm">{{ form.errors.phone }}</span>
        </div>
        <div class="mt-4">
          <label for="experience" class="block text-sm font-medium">Experience</label>
          <textarea v-model="form.experience" id="experience" class="block w-full mt-1"></textarea>
          <span v-if="form.errors.experience" class="text-red-500 text-sm">{{ form.errors.experience }}</span>
        </div>
        <div class="mt-4">
          <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">Update</button>
        </div>
      </form>
    </div>
  </template>
  
  <script setup>
  import { useForm } from '@inertiajs/vue3';
  
  const props = defineProps({
    application: Object
  });
  
  const form = useForm({
    name: props.application.name,
    email: props.application.email,
    phone: props.application.phone,
    experience: props.application.experience
  });
  
  const submit = () => {
    form.put(route('recruitment.update', props.application.id));
  };
  </script>
  