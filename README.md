# Explorador de películas y series

Aplicación web para explorar un catálogo de películas y series, buscar por título, filtrar por tipo, consultar el detalle de cada una y marcar títulos como favoritos.

## Tecnologías seleccionadas

- **Vue.js 3**: framework principal (componentes y reactividad con `ref()`)
- **HTML, CSS y JavaScript**
- **Node.js y npm**: entorno de ejecución y gestor de paquetes


## Instalación y ejecución

**1. Instalar Node.js**

Descargar la versión LTS desde [nodejs.org](https://nodejs.org), dejando marcada la opción **Add to PATH**. Después, abrir una terminal nueva y verificar:

```sh
node -v
npm -v
```

Si ambos comandos muestran una versión, la instalación es correcta.

**2. Crear el proyecto** 

```sh
npm create vue@latest
```

Opciones seleccionadas en el asistente:

| Pregunta | Respuesta |
|---|---|
| Package name | movie-explorer |
| Use TypeScript? | No |
| Features | Ninguna |
| Experimental features | Ninguna |
| Skip all example code? | No |

**3. Instalar dependencias y ejecutar**

Si se clona el repositorio, solo se necesitan estos dos comandos dentro de la carpeta del proyecto:

```sh
npm install
npm run dev  ->Levanta servidor de desarrollo
```

## Componentes

| Componente | Función |
|---|---|
| `App.vue` | Componente raíz. Guarda el estado y arma la página |
| `AppHeader.vue` | Título y botones Catálogo / Favoritos |
| `BarraBusqueda.vue` | Campo de búsqueda por título |
| `FiltrosTipo.vue` | Filtro Todas / Películas / Series |
| `ListaPeliculas.vue` | Cuadrícula de tarjetas (catálogo y favoritos) |
| `TarjetaPelicula.vue` | Imagen, título, género y botón de favorito |
| `DetallePelicula.vue` | Sinopsis, año y duración o temporadas |
| `AppFooter.vue` | Pie de página |
