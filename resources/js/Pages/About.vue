<script setup>
import Mylayout from '@/Layouts/MyLayout.vue';
import { Link, Head } from '@inertiajs/vue3';
import { Inertia } from '@inertiajs/inertia';
import { defineProps } from 'vue';

defineOptions({
    layout: Mylayout
});
</script>

<template>
    <div class="py-12 welcome bg-gray-900 min-h-screen flex items-center justify-center">
        <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
            <div class="bg-gray-800 overflow-hidden shadow-sm sm:rounded-lg">
                <div class="content text-center py-8">
                    <h1 class="text-4xl font-semibold text-white">About Us</h1>
                </div>
                <div class="cont">
                    <div class="story bg-gray-900 text-white p-8 rounded-lg shadow-md">
                        <div class="box">
                            <div class="mini-container">
                                <h1>Our Story</h1>
                                <p>SpaceX, founded in 2002 by Elon Musk, is dedicated to revolutionizing space technology with the ultimate goal of enabling people to live on other planets. With a vision to reduce space transportation costs and make space travel more accessible, SpaceX has achieved numerous historic milestones, including the first privately-funded, liquid-fueled rocket to reach orbit and the first privately-funded company to send a spacecraft to the International Space Station.</p>
                                <h1>Our Mission</h1>
                                <p>Our mission is to revolutionize space technology with the goal of enabling people to live on other planets. We are committed to making space travel more affordable and sustainable, paving the way for the future of interplanetary human exploration. Through relentless innovation and commitment to excellence, we strive to push the boundaries of what is possible and inspire a new era of space exploration.</p>
                            </div>
                            <div class="mini-container">
                                <h1>What We Offer</h1>
                                <ul>
                                    <li>• Advanced Rocket Technology: Our Falcon and Starship rockets are designed for reusability and cost-efficiency, making space access more affordable.</li><br>
                                    <li>• Satellite Deployment: We provide satellite deployment services, enabling a variety of commercial and scientific missions.</li><br>
                                    <li>• Crew Dragon Missions: Our Dragon spacecraft is capable of carrying both cargo and crew to the International Space Station, with future plans for missions to the Moon and Mars.</li><br>
                                    <li>• Mars Colonization: We are actively developing technology to establish a sustainable human presence on Mars, with the goal of making life multiplanetary.</li><br>
                                    <li>• Research and Development: Our continuous R&D efforts focus on innovation in aerospace engineering, propulsion, and materials science.</li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.texts h1 {
    text-shadow: 3px 3px 2px rgb(0, 47, 255);
}

.content h1 {
    text-shadow: 3px 3px 2px rgb(255, 165, 0);
    color: white;
}

.box {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    padding: 20px;
}

.mini-container {
    width: 100%;
    padding: 20px;
}

li {
    text-decoration: none;
}

.story {
    padding: 50px;
    margin-top: 20px;
}

.story h1 {
    font-weight: bolder;
    font-size: 2em;
    margin-bottom: 0.5em;
}

.story p, .story ul {
    font-size: 1.2em;
    margin-bottom: 20px;
    text-align: justify;
}

.story ul {
    list-style-type: none;
    padding-left: 0;
}

.story ul li::before {
    content: '•';
    color: #FFD700; /* gold color */
    font-weight: bold;
    display: inline-block;
    width: 1em;
    margin-left: -1em;
}
</style>
