<script setup>
defineProps({
  pelicula: Object,
  esFavorito: Boolean
})

const emit = defineEmits(['seleccionar', 'alternar-favorito'])
</script>

<template>
  <article class="tarjeta" @click="emit('seleccionar', pelicula)">
    <div class="contenedor-imagen">
      <img
        :src="pelicula.imagen"
        :alt="pelicula.titulo"
        class="tarjeta-imagen"
      />
      <button
        type="button"
        class="boton-favorito"
        :class="{ activo: esFavorito }"
        :title="esFavorito ? 'Quitar de favoritos' : 'Agregar a favoritos'"
        :aria-label="esFavorito ? 'Quitar de favoritos' : 'Agregar a favoritos'"
        @click.stop="emit('alternar-favorito', pelicula.id)"
      >
        <svg
          class="icono-corazon"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"
          />
        </svg>
      </button>
    </div>

    <div class="tarjeta-contenido">
      <span class="tarjeta-tipo">{{ pelicula.tipo }}</span>
      <h3 class="tarjeta-titulo">{{ pelicula.titulo }}</h3>
      <p class="tarjeta-genero">{{ pelicula.genero }}</p>
    </div>
  </article>
</template>

<style scoped>
.tarjeta {
  background-color: #242634;
  border-radius: 10px;
  overflow: hidden;
  border: 1px solid #33364A;
  transition: transform 0.2s ease, border-color 0.2s ease;
  display: flex;
  flex-direction: column;
  cursor: pointer;
  position: relative;
}

.tarjeta:hover {
  transform: translateY(-4px);
  border-color: #38BDF8;
}

.contenedor-imagen {
  position: relative;
  width: 100%;
}

.tarjeta-imagen {
  width: 100%;
  aspect-ratio: 2 / 3;
  object-fit: cover;
  display: block;
  background-color: #1A1B25;
}

.boton-favorito {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  width: 2.2rem;
  height: 2.2rem;
  border-radius: 50%;
  border: 1px solid rgba(255, 255, 255, 0.15);
  background-color: rgba(26, 27, 37, 0.75);
  backdrop-filter: blur(4px);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s ease;
  z-index: 2;
}

.boton-favorito:hover {
  transform: scale(1.1);
  background-color: rgba(26, 27, 37, 0.95);
  border-color: #EF4444;
}

.icono-corazon {
  width: 1.15rem;
  height: 1.15rem;
  fill: #94A3B8;
  transition: fill 0.2s ease;
}

.boton-favorito:hover .icono-corazon {
  fill: #EF4444;
}

.boton-favorito.activo {
  background-color: #EF4444;
  border-color: #EF4444;
}

.boton-favorito.activo .icono-corazon {
  fill: #FFFFFF;
}

.tarjeta-contenido {
  padding: 1rem;
}

.tarjeta-tipo {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  color: #38BDF8;
  margin-bottom: 0.3rem;
}

.tarjeta-titulo {
  font-size: 1.05rem;
  font-weight: 600;
  color: #FFFFFF;
  margin-bottom: 0.35rem;
}

.tarjeta-genero {
  font-size: 0.9rem;
  color: #94A3B8;
}
</style>
