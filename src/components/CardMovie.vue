<template>
    <div class="container text-center">
        <img :src="poster" alt="Movie poster" class="img-fluid rounded-5 w-35 mt-4">
        <h1 class="text-black fw-bold mt-2">{{ titulo }}</h1>
        <h4 class="text-light fw-bold mt-2">{{ descripcion }}</h4>
        <h2 class="text-black fw-bold mt-3">{{ año }}</h2>
        <h3 class="text-light fw-bold mt-3">Actores</h3>
        <h5 class="text-light fw-bold" v-for="a in actores" :key="a.id">{{ a.name }}</h5>
    </div>
</template>

<script setup>
defineProps({
    poster: String,
    titulo: String,
    descripcion: String,
    año: String,
    actores: Array
})
</script>