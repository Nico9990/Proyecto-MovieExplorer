<script setup>
defineProps({
  tipoActual: String
})

const emit = defineEmits(['cambiar-tipo'])

const opciones = [
  { etiqueta: 'Todas', valor: 'Todas' },
  { etiqueta: 'Películas', valor: 'Película' },
  { etiqueta: 'Series', valor: 'Serie' }
]
</script>

<template>
  <div class="filtros-tipo">
    <button
      v-for="opcion in opciones"
      :key="opcion.valor"
      type="button"
      class="boton-filtro"
      :class="{ activo: tipoActual === opcion.valor }"
      @click="emit('cambiar-tipo', opcion.valor)"
    >
      {{ opcion.etiqueta }}
    </button>
  </div>
</template>

<style scoped>
.filtros-tipo {
  display: flex;
  gap: 0.75rem;
  margin-bottom: 2rem;
  flex-wrap: wrap;
}

.boton-filtro {
  padding: 0.6rem 1.25rem;
  font-size: 0.95rem;
  font-weight: 600;
  color: #94A3B8;
  background-color: #242634;
  border: 2px solid #33364A;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.boton-filtro:hover {
  color: #FFFFFF;
  border-color: #38BDF8;
}

.boton-filtro.activo {
  color: #1A1B25;
  background-color: #38BDF8;
  border-color: #38BDF8;
}
</style>
