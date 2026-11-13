<script setup>
defineProps({
  pelicula: Object,
  esFavorito: Boolean
})

const emit = defineEmits(['cerrar', 'alternar-favorito'])
</script>

<template>
  <div class="fondo-modal" @click.self="emit('cerrar')">
    <section class="detalle-tarjeta">
      <button type="button" class="boton-cerrar" @click="emit('cerrar')">
        ✕ Cerrar
      </button>

      <div class="detalle-contenido">
        <img
          :src="pelicula.imagen"
          :alt="pelicula.titulo"
          class="detalle-imagen"
        />

        <div class="detalle-informacion">
          <span class="detalle-etiqueta">{{ pelicula.tipo }}</span>
          <h2 class="detalle-titulo">{{ pelicula.titulo }}</h2>

          <div class="detalle-datos">
            <p><strong>Género:</strong> {{ pelicula.genero }}</p>
            <p><strong>Año:</strong> {{ pelicula.anio }}</p>
            <p>
              <strong>{{ pelicula.tipo === 'Serie' ? 'Temporadas:' : 'Duración:' }}</strong>
              {{ pelicula.duracion }}
            </p>
          </div>

          <div class="detalle-sinopsis">
            <h3>Sinopsis</h3>
            <p>{{ pelicula.sinopsis }}</p>
          </div>

          <button
            type="button"
            class="boton-favorito-detalle"
            :class="{ activo: esFavorito }"
            @click="emit('alternar-favorito', pelicula.id)"
          >
            <span class="icono-favorito-detalle">{{ esFavorito ? '❤️' : '🤍' }}</span>
            <span>{{ esFavorito ? 'Quitar de favoritos' : 'Agregar a favoritos' }}</span>
          </button>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.fondo-modal {
  position: fixed;
  inset: 0;
  background-color: rgba(26, 27, 37, 0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
  z-index: 100;
}

.detalle-tarjeta {
  background-color: #242634;
  border: 1px solid #33364A;
  border-radius: 12px;
  max-width: 760px;
  width: 100%;
  padding: 1.75rem;
  position: relative;
}

.boton-cerrar {
  position: absolute;
  top: 1.25rem;
  right: 1.25rem;
  background-color: #1A1B25;
  color: #94A3B8;
  border: 1px solid #33364A;
  border-radius: 6px;
  padding: 0.4rem 0.85rem;
  font-size: 0.9rem;
  cursor: pointer;
  transition: color 0.2s ease, border-color 0.2s ease;
}

.boton-cerrar:hover {
  color: #FFFFFF;
  border-color: #38BDF8;
}

.detalle-contenido {
  display: flex;
  gap: 1.75rem;
  align-items: flex-start;
}

.detalle-imagen {
  width: 220px;
  aspect-ratio: 2 / 3;
  object-fit: cover;
  border-radius: 8px;
  background-color: #1A1B25;
  flex-shrink: 0;
}

.detalle-informacion {
  flex: 1;
}

.detalle-etiqueta {
  display: inline-block;
  font-size: 0.8rem;
  font-weight: 600;
  color: #1A1B25;
  background-color: #38BDF8;
  padding: 0.2rem 0.65rem;
  border-radius: 6px;
  margin-bottom: 0.6rem;
}

.detalle-titulo {
  font-size: 1.6rem;
  color: #FFFFFF;
  margin-bottom: 1rem;
  padding-right: 5rem;
}

.detalle-datos {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  color: #94A3B8;
  margin-bottom: 1.25rem;
  font-size: 0.95rem;
}

.detalle-datos strong {
  color: #FFFFFF;
}

.detalle-sinopsis h3 {
  font-size: 1.05rem;
  color: #38BDF8;
  margin-bottom: 0.4rem;
}

.detalle-sinopsis p {
  color: #FFFFFF;
  line-height: 1.6;
}

.boton-favorito-detalle {
  margin-top: 1.25rem;
  padding: 0.6rem 1.25rem;
  font-size: 0.95rem;
  font-weight: 600;
  color: #FFFFFF;
  background-color: #1A1B25;
  border: 1px solid #33364A;
  border-radius: 8px;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  transition: all 0.2s ease;
}

.boton-favorito-detalle:hover {
  border-color: #EF4444;
}

.boton-favorito-detalle.activo {
  background-color: #EF4444;
  border-color: #EF4444;
}

.icono-favorito-detalle {
  font-size: 1.1rem;
}

@media (max-width: 600px) {
  .detalle-contenido {
    flex-direction: column;
    align-items: center;
  }

  .detalle-imagen {
    width: 170px;
  }

  .detalle-titulo {
    padding-right: 0;
  }
}
</style>
