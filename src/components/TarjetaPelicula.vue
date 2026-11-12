<script setup>
defineProps({
  pelicula: Object
})
</script>

<template>
  <article class="tarjeta">
    <img
      :src="pelicula.imagen"
      :alt="pelicula.titulo"
      class="tarjeta-imagen"
    />
    <div class="tarjeta-contenido">
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
}

.tarjeta:hover {
  transform: translateY(-4px);
  border-color: #38BDF8;
}

.tarjeta-imagen {
  width: 100%;
  aspect-ratio: 2 / 3;
  object-fit: cover;
  display: block;
  background-color: #1A1B25;
}

.tarjeta-contenido {
  padding: 1rem;
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
