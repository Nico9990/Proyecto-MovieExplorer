<script setup>
defineProps({
  busqueda: String
})

const emit = defineEmits(['cambiar-busqueda'])
</script>

<template>
  <div class="barra-busqueda">
    <input
      type="text"
      class="campo-busqueda"
      placeholder="Buscar película o serie por título..."
      :value="busqueda"
      @input="emit('cambiar-busqueda', $event.target.value)"
    />
  </div>
</template>

<style scoped>
.barra-busqueda {
  margin-bottom: 2rem;
}

.campo-busqueda {
  width: 100%;
  padding: 0.85rem 1.2rem;
  font-size: 1rem;
  color: #FFFFFF;
  background-color: #242634;
  border: 2px solid #33364A;
  border-radius: 8px;
  outline: none;
  transition: border-color 0.2s ease;
}

.campo-busqueda::placeholder {
  color: #94A3B8;
}

.campo-busqueda:focus {
  border-color: #38BDF8;
}
</style>
