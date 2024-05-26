<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

function handleImageError() {
    document.getElementById('screenshot-container')?.classList.add('hidden');
    document.getElementById('docs-card')?.classList.add('row-span-1');
    document.getElementById('docs-card-content')?.classList.add('flex-row');
    document.getElementById('background')?.classList.add('hidden');
}
</script>

<template>
    <Head title="Welcome" />
    <div class="relative min-h-screen bg-black text-gray-300">
        <img
            id="background"
            class="absolute inset-0 w-full h-full object-cover z-0 opacity-30"
            src="../Components/bg1.avif"
            @error="handleImageError"
        />
        <div class="relative flex flex-col items-center justify-center min-h-screen p-6 selection:bg-gray-500 selection:text-white">
            <div class="relative w-full max-w-2xl lg:max-w-4xl text-center">
                <header class="py-10">
                    <h1 class="text-6xl text-white font-extrabold">SpaceX</h1>
                </header>

                <main class="mt-20">
                    <h2 class="text-4xl text-white font-bold p-4 m-auto rounded-2xl shadow-lg transition duration-500 ease-in-out transform hover:-translate-y-1 hover:scale-105 bg-opacity-50">
    We need man in space!
</h2>

                    <Link 
                        href="/login"
                        class="mt-6 inline-block rounded-md bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 px-6 py-3 text-white font-semibold shadow-lg transition duration-500 ease-in-out transform hover:-translate-y-1 hover:scale-105 focus:outline-none focus-visible:ring-2 focus-visible:ring-white"
                    >
                        Apply Now
                    </Link>
                </main>

                <footer class="mt-10 flex justify-center gap-4">
                    <template v-if="canLogin">
                        <template v-if="$page.props.auth.user">
                            <Link
                                :href="route('dashboard')"
                                class="rounded-md px-3 py-2 bg-gray-800 btn ring-1 ring-transparent transition text-white shadow-lg focus:outline-none focus-visible:ring-2 focus-visible:ring-gray-500"
                            >
                                Dashboard
                            </Link>
                        </template>

                        <template v-else>
                            <div class="flex gap-4">
                                <Link
                                    :href="route('login')"
                                    class="rounded-md px-3 py-2 bg-gray-800 text-white ring-1 ring-transparent transition hover:bg-gray-600 shadow-lg focus:outline-none focus-visible:ring-2 focus-visible:ring-gray-500"
                                >
                                    Log in
                                </Link>

                                <Link
                                    v-if="canRegister"
                                    :href="route('register')"
                                    class="rounded-md px-3 py-2 bg-gray-800 text-white ring-1 ring-transparent transition hover:bg-gray-600 shadow-lg focus:outline-none focus-visible:ring-2 focus-visible:ring-gray-500"
                                >
                                    Register
                                </Link>
                            </div>
                        </template>
                    </template>
                </footer>
            </div>
        </div>
    </div>
</template>

<style scoped>
#background {
    filter: brightness(0.5);
}

header h1 {
    text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.8);
}

main h2 {
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
}

footer a {
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}
</style>
