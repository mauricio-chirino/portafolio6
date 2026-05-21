# App del Tiempo — Módulo 6 (SPA con Vue.js)

Aplicación de una sola página (SPA) construida con **Vue 3** y **Vue Router** que muestra el pronóstico del tiempo para 8 ciudades españolas, consumiendo datos en tiempo real desde la API gratuita **Open-Meteo**.

## Vistas principales

| Vista | Ruta | Descripción |
|-------|------|-------------|
| **Home** | `/` | Lista de 8 ciudades con temperatura actual, icono de clima, humedad y nubosidad. Incluye buscador por nombre. |
| **Detalle** | `/lugar/:id` | Información ampliada: clima actual completo, pronóstico de 7 días, estadísticas semanales y alertas automáticas. |

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
- **`@click`** en tarjetas y botón de volver.
- **`computed`** para el filtrado reactivo de ciudades.
- **`onMounted` / `watch`** para cargar datos de la API al entrar a cada vista.
- **Props y emits** entre `HomeView` → `WeatherCard`.

## Componentes

```
src/
├── App.vue                  # Raíz: navbar + <RouterView>
├── components/
│   └── WeatherCard.vue      # Tarjeta de ciudad
├── views/
│   ├── HomeView.vue         # Vista Home con búsqueda y grid de tarjetas
│   └── DetailView.vue       # Vista Detalle con pronóstico y estadísticas
├── router/
│   └── index.js             # Configuración de rutas
├── services/
│   └── weather.js           # Axios, API Open-Meteo, helpers y constantes
└── assets/
    └── main.css             # Estilos heredados del proyecto original
```

## Datos de la API

Se consumen todos los campos disponibles de **Open-Meteo** (gratuita, sin clave):

- **Actuales:** temperatura, sensación térmica, humedad, precipitación, nubosidad, presión, visibilidad, viento, ráfagas.
- **Diarios (7 días):** tempMax/Min, sensaciónMax/Min, amanecer, atardecer, UV, precipitación, probabilidad de lluvia, vientoMax, ráfagasMax.

Las peticiones se realizan con **axios** usando una instancia configurada con `baseURL`, `timeout` y `paramsSerializer` personalizado.

## Cómo ejecutar

```bash
pnpm install
pnpm dev
```

La app estará disponible en `http://localhost:5173`.

## Historial de commits

| Fecha | Descripción |
|-------|-------------|
| 2026-05-19 09:47 | Inicializar proyecto Vue con pnpm y configurar Vite |
| 2026-05-19 10:53 | Agregar Bootstrap 4 y Bootstrap Icons en index.html |
| 2026-05-19 13:22 | Importar estilos CSS del módulo anterior |
| 2026-05-19 15:38 | Configurar Vue Router con rutas Home y Detalle |
| 2026-05-20 09:14 | Crear servicio de clima con axios y API Open-Meteo |
| 2026-05-20 11:31 | Agregar componente WeatherCard reutilizable |
| 2026-05-20 14:07 | Crear componente raíz App con navbar y footer |
| 2026-05-20 16:42 | Implementar vista Home con buscador y grid de ciudades |
| 2026-05-20 19:05 | Implementar vista Detalle con pronóstico y estadísticas |
| 2026-05-21 11:17 | Agregar README con descripción del proyecto y guía de uso |

## Enlace al repositorio

[https://github.com/mauricio-chirino/portafolio6](https://github.com/mauricio-chirino/portafolio6)
