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
const vista = ref('catalogo')
const seleccionada = ref(null)

const favoritos = ref(JSON.parse(localStorage.getItem('favoritos')) || [])

function alternarFavorito(peliculaId) {
  const indice = favoritos.value.indexOf(peliculaId)
  if (indice === -1) {
    favoritos.value.push(peliculaId)
  } else {
    favoritos.value.splice(indice, 1)
  }
  localStorage.setItem('favoritos', JSON.stringify(favoritos.value))
}

function actualizarBusqueda(nuevoTexto) {
  busqueda.value = nuevoTexto
}

function actualizarTipo(nuevoTipo) {
  tipoFiltro.value = nuevoTipo
}

function cambiarVista(nuevaVista) {
  vista.value = nuevaVista
}

function seleccionarPelicula(pelicula) {
  seleccionada.value = pelicula
}

function cerrarDetalle() {
  seleccionada.value = null
}

const peliculasFiltradas = computed(() => {
  const texto = busqueda.value.trim().toLowerCase()

  const base =
    vista.value === 'favoritos'
      ? peliculas.filter((pelicula) => favoritos.value.includes(pelicula.id))
      : peliculas

  return base.filter((pelicula) => {
    const coincideTitulo = pelicula.titulo.toLowerCase().includes(texto)
    const coincideTipo =
      tipoFiltro.value === 'Todas' || pelicula.tipo === tipoFiltro.value

    return coincideTitulo && coincideTipo
  })
})
</script>

<template>
  <div class="aplicacion">
    <AppHeader
      :vista-actual="vista"
      :cantidad-favoritos="favoritos.length"
      @cambiar-vista="cambiarVista"
    />

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
        :favoritos="favoritos"
        :vista="vista"
        @seleccionar-pelicula="seleccionarPelicula"
        @alternar-favorito="alternarFavorito"
      />

      <DetallePelicula
        v-if="seleccionada"
        :pelicula="seleccionada"
        :es-favorito="favoritos.includes(seleccionada.id)"
        @cerrar="cerrarDetalle"
        @alternar-favorito="alternarFavorito"
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
