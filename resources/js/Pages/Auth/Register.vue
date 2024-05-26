<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Register" />

        <form @submit.prevent="submit" class="max-w-md mx-auto mt-8 p-6 bg-gray-900 bg-opacity-70 rounded-lg shadow-lg">
            <div>
                <InputLabel for="name" value="Name" class="text-gray-400" />

                <TextInput
                    id="name"
                    type="text"
                    class="mt-1 block w-full bg-gray-700 border-gray-600 text-white placeholder-gray-400"
                    v-model="form.name"
                    required
                    autofocus
                    autocomplete="name"
                />

                <InputError class="mt-2" :message="form.errors.name" />
            </div>

            <div class="mt-4">
                <InputLabel for="email" value="Email" class="text-gray-400" />

                <TextInput
                    id="email"
                    type="email"
                    class="mt-1 block w-full bg-gray-700 border-gray-600 text-white placeholder-gray-400"
                    v-model="form.email"
                    required
                    autocomplete="username"
                />

                <InputError class="mt-2" :message="form.errors.email" />
            </div>

            <div class="mt-4">
                <InputLabel for="password" value="Password" class="text-gray-400" />

                <TextInput
                    id="password"
                    type="password"
                    class="mt-1 block w-full bg-gray-700 border-gray-600 text-white placeholder-gray-400"
                    v-model="form.password"
                    required
                    autocomplete="new-password"
                />

                <InputError class="mt-2" :message="form.errors.password" />
            </div>

            <div class="mt-4">
                <InputLabel for="password_confirmation" value="Confirm Password" class="text-gray-400" />

                <TextInput
                    id="password_confirmation"
                    type="password"
                    class="mt-1 block w-full bg-gray-700 border-gray-600 text-white placeholder-gray-400"
                    v-model="form.password_confirmation"
                    required
                    autocomplete="new-password"
                />

                <InputError class="mt-2" :message="form.errors.password_confirmation" />
            </div>

            <div class="flex items-center justify-end mt-6">
                <Link
                    :href="route('login')"
                    class="underline text-sm text-gray-400 hover:text-gray-200 transition duration-300"
                >
                    Already registered?
                </Link>

                <PrimaryButton class="ms-4 bg-gray-700 text-white hover:bg-gray-600 transition duration-300" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                    Register
                </PrimaryButton>
            </div>
        </form>
    </GuestLayout>
</template>

<style scoped>

.max-w-md {
    max-width: 24rem;
}

.text-gray-400 {
    color: #cbd5e0;
}

.placeholder-gray-400::placeholder {
    color: #a0aec0;
}

.hover\:bg-gray-600:hover {
    background-color: #2d3748;
}

.hover\:text-gray-200:hover {
    color: #e2e8f0;
}
</style>
