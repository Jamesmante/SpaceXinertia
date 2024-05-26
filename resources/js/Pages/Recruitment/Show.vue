<template>
    <div>
      <h1 class="text-3xl font-semibold mb-6">Application Details</h1>
      <p><strong>Name:</strong> {{ application.name }}</p>
      <p><strong>Email:</strong> {{ application.email }}</p>
      <p><strong>Phone:</strong> {{ application.phone }}</p>
      <p><strong>Experience:</strong> {{ application.experience }}</p>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    application: Object
  });
  </script>
  