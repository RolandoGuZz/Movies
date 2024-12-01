<template>
    <div class="container text-center mt-4">
        <button class="btn btn-outline-light btn-lg me-2" @click="backMovies" :disabled="inicio <= 0 ? true : false">Back</button>
        <button class="btn btn-outline-light btn-lg" @click="nextMovies" :disabled="final >= 20 ? true : false">Next</button>

        <div class="row">
            <div class="col text-center text-bg-secondary rounded-5 mt-4 me-5" v-for="m in data.slice(inicio, final)" :key="m.id">
                <CardMovie 
                    :poster="`https://image.tmdb.org/t/p/w500${m.poster_path}`" 
                    :titulo="m.title" 
                    :descripcion="m.overview" 
                    :año="m.release_date" 
                    :actores="actors[m.id]"
                />
            </div>
        </div>
    </div>
</template>

<script setup>
    import CardMovie from './CardMovie.vue';
    import { ref } from 'vue';
    const moviesURL = "https://api.themoviedb.org/3/movie/popular?api_key=9e3311ec1f57418cb454df1bde326ff2"

    const data = ref([]);
    const actors = ref([]);

    const getMovies = async () =>{
        try{
            const resp = await fetch(moviesURL);
            const movies = await resp.json();
            data.value = movies.results;
            data.value.forEach(movie =>{
                getActors(movie.id);
            })
        }catch(error){
            console.log(error);
            return[];
        }
    }

    const getActors = async (id) =>{
        try{
            const resp = await fetch(`https://api.themoviedb.org/3/movie/${id}/credits?api_key=9e3311ec1f57418cb454df1bde326ff2`);
            const actorsData = await resp.json();
            actors.value[id] = actorsData.cast.slice(0,5);
        }catch(error){
            console.log(error);
        }
    }

    const valor = 2;
    const inicio = ref(0);
    const final = ref(valor);

    const nextMovies = () =>{
        inicio.value += valor;
        final.value += valor;
    }

    const backMovies = () =>{
        inicio.value -= valor;
        final.value -= valor;
    }

    getMovies();
</script>