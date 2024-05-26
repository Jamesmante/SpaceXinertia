<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Log in" />
        <div class="fixed inset-0 flex items-center justify-center bg-gray-900 text-gray-300">
            <div class="max-w-md w-full bg-gray-800 bg-opacity-70 rounded-lg p-8 shadow-lg">
                <div v-if="status" class="mb-4 font-medium text-sm text-green-500">
                    {{ status }}
                </div>

                <form @submit.prevent="submit" class="mt-6">
                    <div>
                        <InputLabel for="email" value="Email" class="text-gray-400" />
                        <TextInput
                            id="email"
                            type="email"
                            class="mt-1 block w-full bg-gray-700 border-gray-600 text-white placeholder-gray-400"
                            v-model="form.email"
                            required
                            autofocus
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
                            autocomplete="current-password"
                        />
                        <InputError class="mt-2" :message="form.errors.password" />
                    </div>

                    <div class="block mt-4">
                        <label class="flex items-center text-gray-400">
                            <Checkbox name="remember" v-model:checked="form.remember" />
                            <span class="ms-2 text-sm">Remember me</span>
                        </label>
                    </div>

                    <div class="flex items-center justify-between mt-6">
                        <Link
                            v-if="canResetPassword"
                            :href="route('password.request')"
                            class="underline text-sm text-gray-400 hover:text-gray-200 transition duration-300"
                        >
                            Forgot your password?
                        </Link>

                        <PrimaryButton class="ms-4 bg-gray-700 text-white hover:bg-gray-600 transition duration-300" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Log in
                        </PrimaryButton>
                    </div>
                </form>
            </div>
        </div>
    </GuestLayout>
</template>

<style scoped>
/* Custom styling */
/* Change background color of the page */
.bg-gray-900 {
    background-color: #1a202c;
}

/* Style the form container */
.max-w-md {
    max-width: 24rem;
}

/* Style the input fields and labels */
.text-gray-400 {
    color: #cbd5e0;
}

.placeholder-gray-400::placeholder {
    color: #a0aec0;
}

.hover\:bg-gray-600:hover {
    background-color: #2d3748;
}

/* Style the forgot password link */
.text-gray-400 {
    color: #cbd5e0;
}

.hover\:text-gray-200:hover {
    color: #e2e8f0;
}
</style>
