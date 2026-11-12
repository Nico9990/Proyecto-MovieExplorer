<script setup>
import { ref, computed } from 'vue'
import { peliculas } from './data/peliculas.js'
import AppHeader from './components/AppHeader.vue'
import BarraBusqueda from './components/BarraBusqueda.vue'
import FiltrosTipo from './components/FiltrosTipo.vue'
import ListaPeliculas from './components/ListaPeliculas.vue'
import DetallePelicula from './components/DetallePelicula.vue'

const busqueda = ref('')
const tipoFiltro = ref('Todas')
const seleccionada = ref(null)

function actualizarBusqueda(nuevoTexto) {
  busqueda.value = nuevoTexto
}

function actualizarTipo(nuevoTipo) {
  tipoFiltro.value = nuevoTipo
}

function seleccionarPelicula(pelicula) {
  seleccionada.value = pelicula
}

function cerrarDetalle() {
  seleccionada.value = null
}

const peliculasFiltradas = computed(() => {
  const texto = busqueda.value.trim().toLowerCase()

  return peliculas.filter((pelicula) => {
    const coincideTitulo = pelicula.titulo.toLowerCase().includes(texto)
    const coincideTipo =
      tipoFiltro.value === 'Todas' || pelicula.tipo === tipoFiltro.value

    return coincideTitulo && coincideTipo
  })
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

      <FiltrosTipo
        :tipo-actual="tipoFiltro"
        @cambiar-tipo="actualizarTipo"
      />

      <ListaPeliculas
        :peliculas="peliculasFiltradas"
        @seleccionar-pelicula="seleccionarPelicula"
      />

      <DetallePelicula
        v-if="seleccionada"
        :pelicula="seleccionada"
        @cerrar="cerrarDetalle"
      />
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
