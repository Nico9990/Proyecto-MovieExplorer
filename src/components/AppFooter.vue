<script setup>
const anioActual = new Date().getFullYear()
</script>

<template>
  <footer class="pie-pagina">
    <div class="contenedor-pie">
      <div class="pie-info">
        <h3 class="pie-titulo">Cinéverso</h3>
        <p class="pie-descripcion">
          Explorador de películas y series desarrollado con Vue.js 3.
        </p>
      </div>

      <div class="pie-creditos">
        <p class="pie-copyright">
          © {{ anioActual }} Cinéverso. Proyecto de desarrollo web.
        </p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.pie-pagina {
  background-color: #242634;
  border-top: 1px solid #33364A;
  padding: 2rem 1.5rem;
  margin-top: 3rem;
}

.contenedor-pie {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 1rem;
}

.pie-titulo {
  font-size: 1.3rem;
  font-weight: 700;
  color: #38BDF8;
  margin-bottom: 0.3rem;
}

.pie-descripcion {
  color: #94A3B8;
  font-size: 0.95rem;
}

.pie-creditos {
  border-top: 1px solid #33364A;
  width: 100%;
  padding-top: 1rem;
}

.pie-copyright {
  color: #64748B;
  font-size: 0.85rem;
}
</style>
