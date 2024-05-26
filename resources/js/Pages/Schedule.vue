<script setup>
import Mylayout from '@/Layouts/MyLayout.vue';
import { Link, Head } from '@inertiajs/vue3';
import { Inertia } from '@inertiajs/inertia';
import { defineProps } from 'vue';

const props = defineProps ({
    events: Array
})

defineOptions({
    layout: Mylayout
});

</script>

<template>
    <div class="py-12 welcome">
        <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
            <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                <div class="text-container">
                    <div class="text">
                        <h1>Schedules</h1>
                        <p>Discover the upcoming SpaceX events and missions. Stay tuned for launch dates, venues, and more details.</p>
                    </div>
                </div>
                <div class="outer-container">
                    <div class="container">
                        <div class="card">
                            <h1>Starlink Mission</h1>
                            <h2>Venue: Kennedy Space Center</h2>
                            <h4>Address: Florida, USA</h4>
                            <table>
                                <tr>
                                    <th>Start of Event</th>
                                    <th>End of Event</th>
                                </tr>
                                <tr>
                                    <td>2024-06-12 14:30</td>
                                    <td>2024-06-12 16:30</td>
                                </tr>
                            </table>
                        </div>
                        <div class="card">
                            <h1>CRS-24 Mission</h1>
                            <h2>Venue: Cape Canaveral</h2>
                            <h4>Address: Florida, USA</h4>
                            <table>
                                <tr>
                                    <th>Start of Event</th>
                                    <th>End of Event</th>
                                </tr>
                                <tr>
                                    <td>2024-07-08 12:00</td>
                                    <td>2024-07-08 14:00</td>
                                </tr>
                            </table>
                        </div>
                        <div class="card">
                            <h1>GPS III SV05</h1>
                            <h2>Venue: Cape Canaveral</h2>
                            <h4>Address: Florida, USA</h4>
                            <table>
                                <tr>
                                    <th>Start of Event</th>
                                    <th>End of Event</th>
                                </tr>
                                <tr>
                                    <td>2024-08-20 10:00</td>
                                    <td>2024-08-20 12:00</td>
                                </tr>
                            </table>
                        </div>
                    </div>
                    <div class="container">
                        <div class="contents" v-for="event in events" :key="event.id">
                            <div class="box1">
                                <h1>{{ event.name }}</h1><br>
                                <h2>Venue: {{ event.venue }}</h2><br>
                                <h4>Address: {{ event.place }}</h4>
                            </div>
                            <table>
                                <tr>
                                    <th>Start of Event</th>
                                    <th>End of Event</th>
                                </tr>
                                <tr>
                                    <td>{{ event.timestart }}</td>
                                    <td>{{ event.timeend }}</td>
                                </tr>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.welcome {
    background-color: gray;
}

.text-container {
    padding: 20px;
    text-align: center;
}

.text {
    text-shadow: 3px 3px 2px rgb(255, 165, 0);
    color: black;
    font-size: 30px;
    text-align: center;
    margin-bottom: 20px;
}

.outer-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.container {
    display: grid;
    grid-template-columns: repeat(3, minmax(200px, 1fr));
    gap: 20px;
    padding: 20px;
}

.card, .contents {
    background-color: white;
    border-radius: 20px;
    padding: 50px;
    margin-bottom: 20px;
    box-shadow: rgba(0, 0, 0, 0.4) 0px 2px 4px, rgba(0, 0, 0, 0.3) 0px 7px 13px -3px, rgba(0, 0, 0, 0.2) 0px -3px 0px inset;
}

.card h1, .box1 h1 {
    font-size: 40px;
    font-weight: bold;
}

.card h2, .box1 h2 {
    font-size: 20px;
    font-weight: bold;
}

table {
    font-family: arial, sans-serif;
    border-collapse: collapse;
    width: 50%;
}
  
td, th {
    border: 1px solid #dddddd;
    text-align: left;
    text-align: center;
    padding: 8px;
}
  
td {
    background-color: lightgray;
}
  
th {
    background-color: rgb(203, 240, 203);
}
</style>
