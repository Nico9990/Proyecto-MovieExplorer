<script setup>
import TarjetaPelicula from './TarjetaPelicula.vue'

defineProps({
  peliculas: {
    type: Array,
    default: () => []
  },
  favoritos: {
    type: Array,
    default: () => []
  },
  vista: {
    type: String,
    default: 'catalogo'
  }
})

const emit = defineEmits(['seleccionar-pelicula', 'alternar-favorito'])
</script>

<template>
  <section class="lista-peliculas">
    <p v-if="peliculas.length === 0" class="mensaje-vacio">
      {{
        vista === 'favoritos'
          ? 'Aún no has agregado ninguna película o serie a tus favoritos.'
          : 'No se encontraron películas o series con esos criterios.'
      }}
    </p>

    <div v-else class="cuadricula-tarjetas">
      <TarjetaPelicula
        v-for="item in peliculas"
        :key="item.id"
        :pelicula="item"
        :es-favorito="favoritos.includes(item.id)"
        @seleccionar="emit('seleccionar-pelicula', $event)"
        @alternar-favorito="emit('alternar-favorito', $event)"
      />
    </div>
  </section>
</template>

<style scoped>
.cuadricula-tarjetas {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
  gap: 1.5rem;
}

.mensaje-vacio {
  text-align: center;
  color: #94A3B8;
  font-size: 1.1rem;
  padding: 3rem 1rem;
  background-color: #242634;
  border-radius: 10px;
}
</style>
