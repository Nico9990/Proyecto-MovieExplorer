<script setup>
defineProps({
  vistaActual: {
    type: String,
    default: 'catalogo'
  },
  cantidadFavoritos: {
    type: Number,
    default: 0
  }
})

const emit = defineEmits(['cambiar-vista'])
</script>

<template>
  <header class="encabezado">
    <div class="contenedor-encabezado">
      <h1 class="titulo-sitio" @click="emit('cambiar-vista', 'catalogo')">Cinéverso</h1>

      <nav class="navegacion">
        <button
          type="button"
          class="boton-nav"
          :class="{ activo: vistaActual === 'catalogo' }"
          @click="emit('cambiar-vista', 'catalogo')"
        >
          Catálogo
        </button>

        <button
          type="button"
          class="boton-nav"
          :class="{ activo: vistaActual === 'favoritos' }"
          @click="emit('cambiar-vista', 'favoritos')"
        >
          Favoritos
          <span v-if="cantidadFavoritos > 0" class="contador-favoritos">
            {{ cantidadFavoritos }}
          </span>
        </button>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.encabezado {
  background-color: #242634;
  border-bottom: 1px solid #33364A;
  padding: 1rem 2rem;
}

.contenedor-encabezado {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.titulo-sitio {
  font-size: 1.8rem;
  font-weight: 700;
  color: #38BDF8;
  letter-spacing: 0.5px;
  cursor: pointer;
  user-select: none;
}

.navegacion {
  display: flex;
  gap: 0.75rem;
}

.boton-nav {
  padding: 0.5rem 1.1rem;
  font-size: 0.95rem;
  font-weight: 600;
  color: #94A3B8;
  background-color: #1A1B25;
  border: 1px solid #33364A;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
}

.boton-nav:hover {
  color: #FFFFFF;
  border-color: #38BDF8;
}

.boton-nav.activo {
  color: #1A1B25;
  background-color: #38BDF8;
  border-color: #38BDF8;
}

.contador-favoritos {
  background-color: #EF4444;
  color: #FFFFFF;
  font-size: 0.75rem;
  font-weight: 700;
  padding: 0.1rem 0.45rem;
  border-radius: 9999px;
  line-height: 1.2;
}

.boton-nav.activo .contador-favoritos {
  background-color: #1A1B25;
  color: #38BDF8;
}
</style>
