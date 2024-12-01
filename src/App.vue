<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-black">
        <div class="container-fluid">
            <a class="navbar-brand">MOVIES</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#colapso">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="colapso">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link">Inicio</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link">Contacto</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link">Perfil</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

  <MovieApi />

  <footer class="bg-black text-light mt-4 pt-4 pb-3">
    <div class="container text-center">
      <p>© 2024 Popular Movies. Derechos reservados.</p>
    </div>
  </footer>
</template>

<script setup>
import MovieApi from './components/MovieApi.vue';
</script>