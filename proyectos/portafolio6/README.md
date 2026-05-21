# App del Tiempo — Módulo 6 (SPA con Vue.js)

Aplicación de una sola página (SPA) construida con **Vue 3** y **Vue Router** que muestra el pronóstico del tiempo para 8 ciudades españolas, consumiendo datos en tiempo real desde la API gratuita **Open-Meteo**.

## Vistas principales

| Vista | Ruta | Descripción |
|-------|------|-------------|
| **Home** | `/` | Lista de 8 ciudades con temperatura actual, icono de clima y viento. Incluye buscador por nombre y selector de unidad (°C / °F). |
| **Detalle** | `/lugar/:id` | Información ampliada del lugar: clima actual, pronóstico de 7 días, estadísticas semanales (min, max, promedio) y alertas automáticas. |

## Rutas configuradas (Vue Router)

```
/           → HomeView    (lista de ciudades)
/lugar/:id  → DetailView  (detalle dinámico por ID)
```

## Funcionalidades Vue usadas

- **Interpolación** `{{ }}` para mostrar nombres, temperaturas y descripciones.
- **`v-for`** para renderizar la lista de ciudades y los días del pronóstico.
- **`v-if` / `v-else`** para mostrar estados de carga, error y contenido.
- **`v-show`** para el enlace "Detalle" en la navbar (visible solo en esa ruta).
- **`v-model`** en el input de búsqueda (two-way binding reactivo).
- **`@click`** en tarjetas, botones de unidad y botón de volver.
- **`computed`** para el filtrado reactivo de ciudades y la conversión de temperatura.
- **`onMounted` / `watch`** para cargar datos de la API al entrar a cada vista.
- **Props y emits** entre `HomeView` → `WeatherCard`.

## Componentes

```
src/
├── App.vue                  # Raíz: navbar + <RouterView>
├── components/
│   └── WeatherCard.vue      # Tarjeta de ciudad (acepta prop unidad)
├── views/
│   ├── HomeView.vue         # Vista Home con búsqueda y grid de tarjetas
│   └── DetailView.vue       # Vista Detalle con pronóstico y estadísticas
├── router/
│   └── index.js             # Configuración de rutas
├── services/
│   └── weather.js           # API Open-Meteo, helpers y constantes
└── assets/
    └── main.css             # Estilos heredados del proyecto original
```

## Cómo ejecutar

```bash
pnpm install
pnpm dev
```

La app estará disponible en `http://localhost:5173`.

## Enlace al repositorio

[https://github.com/mauricio-chirino/binding-formulario](https://github.com/mauricio-chirino/binding-formulario)
