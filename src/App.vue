<script setup>
import { ref, computed } from 'vue'
import { peliculas } from './data/peliculas.js'
import AppHeader from './components/AppHeader.vue'
import BarraBusqueda from './components/BarraBusqueda.vue'
import ListaPeliculas from './components/ListaPeliculas.vue'

const busqueda = ref('')

function actualizarBusqueda(nuevoTexto) {
  busqueda.value = nuevoTexto
}

const peliculasFiltradas = computed(() => {
  const texto = busqueda.value.trim().toLowerCase()
  if (!texto) {
    return peliculas
  }
  return peliculas.filter((pelicula) =>
    pelicula.titulo.toLowerCase().includes(texto)
  )
})
</script>

<template>
  <div class="aplicacion">
    <AppHeader />

    <main class="contenido-principal">
      <BarraBusqueda
        :busqueda="busqueda"
        @cambiar-busqueda="actualizarBusqueda"
      />

      <ListaPeliculas :peliculas="peliculasFiltradas" />
    </main>
  </div>
</template>

<style scoped>
.aplicacion {
  min-height: 100vh;
  background-color: #1A1B25;
}

.contenido-principal {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}
</style>
