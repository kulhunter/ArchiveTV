# ArchiveTV 🍿

ArchiveTV es una aplicación web ligera construida con Vanilla JS, HTML y CSS. Transforma el vasto repositorio público de televisión y noticias de [Internet Archive](https://archive.org) en una experiencia de usuario moderna, fluida y similar a plataformas de streaming comerciales como Netflix.

## 🚀 Características Principales

* **Interfaz de Streaming (UI/UX):** Diseño oscuro, *hero banner* destacado y carruseles de navegación horizontal con animaciones de escalado al pasar el mouse.
* **Reproductor Integrado (Modal):** Al hacer clic en un título, el video se abre en una ventana modal cinematográfica con reproducción automática, evitando redirigir al usuario a otras pestañas.
* **Sincronización Continua:** La aplicación consulta la API automáticamente cada 60 segundos para añadir las transmisiones que se acaban de subir a Internet Archive.
* **Actualizaciones Silenciosas:** Si el usuario tiene el reproductor abierto, la aplicación detiene temporalmente el redibujado de la pantalla para no interrumpir la experiencia de visualización.
* **Limpieza de Metadatos:** Filtra y formatea las descripciones de la base de datos (eliminando etiquetas de código sobrantes) para mostrar sinopsis limpias, junto con el nombre del creador y el año.

## 🛠️ Tecnologías Utilizadas

* **HTML5:** Estructura semántica de la interfaz.
* **CSS3:** Estilos puros, variables nativas, *Flexbox* para la disposición de elementos y *Media Queries* para garantizar que funcione en móviles, tablets y escritorio.
* **Vanilla JavaScript (ES6+):** Lógica del lado del cliente, manipulación del DOM y consumo de la API mediante `async/await` y `fetch`.
* **API de Internet Archive:** Fuente de datos (metadatos, imágenes y *embeds* de video).

## ⚙️ Instalación y Uso

Este proyecto es de naturaleza "cero dependencias". No necesitas instalar Node.js, NPM, ni configurar compiladores como Webpack o Vite.

1. Clona este repositorio en tu máquina local o descarga el archivo `index.html`.
2. Haz doble clic sobre el archivo `index.html` para abrirlo en cualquier navegador web moderno (Chrome, Firefox, Safari, Edge, Brave).
3. ¡Listo! La app se conectará automáticamente y empezará a mostrar el catálogo.

## 📡 Bajo el capó: La API

La aplicación realiza peticiones al *endpoint* de búsqueda avanzada de Internet Archive (`advancedsearch.php`). 

Busca específicamente dentro de las colecciones `tv` y `tvnews`, solicitando un máximo de 61 resultados ordenados desde el más reciente al más antiguo (`sort[]=addeddate+desc`). A partir del `identifier` único que devuelve el JSON, el código deduce las rutas exactas de los recursos:
* **Miniaturas:** `https://archive.org/services/img/{identifier}`
* **Reproductor de video:** `https://archive.org/embed/{identifier}`

## ⚠️ Consideraciones y Limitaciones

* **Dependencia de Servidores:** La velocidad de carga de las imágenes y el *buffering* de los videos dependen exclusivamente del estado y la saturación de los servidores de Internet Archive.
* **Disponibilidad de Datos:** Algunos videos históricos o transmisiones muy recientes pueden carecer de sinopsis o miniaturas completas. La aplicación maneja estos casos con imágenes de respaldo y textos por defecto.
