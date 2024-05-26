<script setup>
import MyLayout from '@/Layouts/MyLayout.vue';
import { Head, Link } from '@inertiajs/vue3';


defineProps({
    // Define any props if needed
});

defineOptions({
    layout: MyLayout
});
</script>

<template>
  <div class="py-12 welcome bg-gray-900 min-h-screen flex items-center justify-center">
    <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
      <div class="bg-gray-900 overflow-hidden shadow-sm sm:rounded-lg">
        <div class="content text-center">
          <div class="info">
            <div class="texts">
              <h1 class="text-4xl font-semibold text-white">Join SpaceX's Next Mission</h1>
            </div>
          </div>
        </div>
        <div class="about">
          <div class="firstsection">
            <h1 class="text-3xl font-semibold text-white mb-4">Become a SpaceX Astronaut</h1>
            <p class="text-lg text-gray-300 leading-relaxed">Are you ready to take your career to new heights? SpaceX is seeking highly motivated individuals to join our team of astronauts. As part of SpaceX, you'll be at the forefront of human space exploration, contributing to missions that will pave the way for the future of humanity in space.</p>
            <h2 class="text-2xl font-semibold text-white mt-6 mb-2">Recruitment Process</h2>
            <p class="text-lg text-gray-300 leading-relaxed">Our recruitment process is designed to identify the best and brightest candidates who are passionate about space exploration. The process includes multiple stages of assessment, including technical evaluations, physical fitness tests, and interviews with our top engineers and scientists.</p>
            <h2 class="text-2xl font-semibold text-white mt-6 mb-2">Requirements</h2>
            <ul class="text-lg text-gray-300 leading-relaxed list-disc list-inside">
              <li>Bachelor’s degree in Engineering, Science, or related field.</li>
              <li>At least three years of related professional experience or 1,000 hours of pilot-in-command time in jet aircraft.</li>
              <li>Excellent physical condition and ability to pass NASA’s long-duration spaceflight physical.</li>
              <li>Strong skills in leadership, teamwork, and communication.</li>
            </ul>
            <h2 class="text-2xl font-semibold text-white mt-6 mb-2">Join Us</h2>
            <p class="text-lg text-gray-300 leading-relaxed">If you meet these qualifications and are eager to contribute to our mission, we invite you to apply. Together, we can make life multiplanetary and explore the final frontier. Apply now and be part of the next giant leap for mankind!</p>
            <!-- Add Apply Now Button -->
            <div class="mt-8">
              <Link :href="route('recruitment.create')" class="bg-orange-500 text-white px-4 py-2 rounded hover:bg-orange-600">
                Apply Now
              </Link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.texts h1 {
    text-shadow: 3px 3px 2px rgb(255, 165, 0);
}

.about {
    background-color: rgba(255, 255, 255, 0.1);
    text-align: center;
    padding: 50px;
    border-radius: 10px;
    margin: 20px;
}

.about p, .about ul {
    font-size: 1.2em;
    margin-bottom: 20px;
    text-align: justify;
}

.about h1, .about h2 {
    font-weight: bolder;
    font-size: 2em;
    margin-bottom: 0.5em;
}

.about h2 {
    font-size: 1.5em;
}

.info {
    color: white;
    padding: 50px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.content {
    padding: 50px 0;
}
</style>
