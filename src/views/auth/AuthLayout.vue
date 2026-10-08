<script setup>
    import { useRoute } from 'vue-router'
    const route = useRoute()

    const authRoutes = [
        { name: 'register', text: 'Crear una cuenta' },
        { name: 'login', text: 'Iniciar Sesión' },
        { name: 'forgot-password', text: 'Olvide mi password' },
    ]
</script>

<template>
    <div class="mx-auto lg:w-3/5 mt-20">
        <RouterView />

        <nav class="mt-10 flex flex-col items-center space-y-5 lg:flex-row lg:justify-between lg:space-y-0">
            <RouterLink
                v-for="authRoute in authRoutes"
                class="uppercase font-bold text-white"
                :to="{name: authRoute.name}"
                :class="{ 'hidden' : route.name === authRoute.name }"
            >{{ authRoute.text }}</RouterLink>
        </nav>

        <!-- Eliminar este aviso en producción -->
        <div class="mx-auto mt-20 border border-blue-500/20 p-5 rounded-lg bg-blue-500/20">
            <p class="text-center text-white">
                Este es un proyecto de prueba, por lo tanto, las opciones "Crear una cuenta" y "Olvide mi password" no están disponibles. Utiliza <b>demo@prueba.com</b> y <b>12345678</b> para iniciar sesión.
            </p>
        </div>
    </div>
</template>
