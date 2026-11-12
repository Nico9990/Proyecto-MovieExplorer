<script setup>
import TarjetaPelicula from './TarjetaPelicula.vue'

defineProps({
  peliculas: Array
})

const emit = defineEmits(['seleccionar-pelicula'])
</script>

<template>
  <section class="lista-peliculas">
    <p v-if="peliculas.length === 0" class="mensaje-vacio">
      No se encontraron películas o series con esos criterios.
    </p>

    <div v-else class="cuadricula-tarjetas">
      <TarjetaPelicula
        v-for="item in peliculas"
        :key="item.id"
        :pelicula="item"
        @seleccionar="emit('seleccionar-pelicula', $event)"
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
