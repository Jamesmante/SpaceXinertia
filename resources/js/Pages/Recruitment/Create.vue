<template>
  <div>
    <h1 class="text-3xl font-semibold mb-6">Apply for Astronaut</h1>
    <form @submit.prevent="submitForm">
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
        <button v-if="!isEditing" type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">Submit</button>
        <button v-else type="button" @click="updateApplication" class="bg-green-500 text-white px-4 py-2 rounded">Update</button>
      </div>
    </form>

    <div class="mt-8">
      <h2 class="text-xl font-semibold mb-4">Submitted Applications</h2>
      <div v-if="applications.length === 0" class="text-gray-500">No applications submitted yet.</div>
      <div v-else>
        <div v-for="(application, index) in applications" :key="index" class="bg-white shadow-md rounded-lg p-4 mb-4">
          <h3 class="text-lg font-semibold">{{ application.name }}</h3>
          <p><strong>Email:</strong> {{ application.email }}</p>
          <p><strong>Phone:</strong> {{ application.phone }}</p>
          <p><strong>Experience:</strong> {{ application.experience }}</p>
          <div class="mt-2">
            <button @click="editApplication(index)" class="text-blue-500 mr-2">{{ isEditing && editIndex === index ? 'Cancel' : 'Edit' }}</button>
            <button @click="deleteApplication(index)" class="text-red-500">Delete</button>
          </div>
        </div>
      </div>
    </div>

    <button @click="returnToDashboard" class="bg-gray-500 text-white px-4 py-2 rounded mt-8">Return to Dashboard</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useForm } from '@inertiajs/vue3';
import { Inertia } from '@inertiajs/inertia';

const form = useForm({
  name: '',
  email: '',
  phone: '',
  experience: '',
  errors: {}
});

const applications = ref([]);

const isEditing = ref(false);
const editIndex = ref(null);

const submitForm = async () => {
  try {
    const applicationData = { ...form };
    applications.value.push(applicationData);
    form.reset(); // Reset the form fields after submission
    console.log('Form submitted successfully:', applicationData);
  } catch (error) {
    console.error('Error submitting form:', error);
  }
};

const editApplication = (index) => {
  if (isEditing.value && editIndex.value === index) {
    isEditing.value = false;
    editIndex.value = null;
    form.reset(); // Reset the form when cancelling edit
  } else {
    isEditing.value = true;
    editIndex.value = index;
    const application = applications.value[index];
    form.name = application.name;
    form.email = application.email;
    form.phone = application.phone;
    form.experience = application.experience;
  }
};

const updateApplication = () => {
  applications.value[editIndex.value] = { ...form };
  form.reset(); // Reset the form after updating
  isEditing.value = false;
  editIndex.value = null;
};

const deleteApplication = (index) => {
  applications.value.splice(index, 1);
  console.log('Delete application:', index);
};

const returnToDashboard = () => {
  Inertia.visit(route('/dashboard')); // Corrected navigation using Inertia.js
};
</script>
