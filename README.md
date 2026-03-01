## 🇬🇧 English

# 🔍 DupeCleaner

Browser-based duplicate file finder. No server, no uploads — 100% local. Pick a folder, the app recursively scans every file using SHA-256, groups identical copies by content and shows them in real time so you can review and delete them without leaving the tab.

---

## Features

- Size pre-filter — files with different sizes are skipped before any I/O
- Smart sampling — for files above 20 MB, reads only three 2 MB slices (start · middle · end), capped at 6 MB of RAM regardless of file size
- Inline Web Worker — SHA-256 runs off the main thread, UI stays responsive throughout
- Native preview — images, text, code, PDF, video and audio
- Configurable scan — ignore dev folders, hidden files, system extensions; set a minimum file size
- Format filter chips — filter duplicate groups by file extension in one click
- Dark / Light theme, persisted in `localStorage`
- Responsive — collapsible feed panel, floating FAB, works on Android Chrome
- Firefox / Safari — scan only (no deletion, browser limitation)
- Zero dependencies — one `.html` file, no build step, no `npm install`

## Requirements

A modern browser. Chrome 86+ or Edge 86+ for full functionality (scan + delete). Firefox and Safari for scan only.

## Run it

No installation needed. Open `index.html` directly in your browser, or use the live version:

```
https://jaimefg1888.github.io/DupeCleaner/
```

### Controls

| Action | How |
|--------|-----|
| Pick folder | Click "Seleccionar carpeta" |
| Stop scan | Click "Detener" in the nav bar |
| Preview file | Click the 👁 eye button on any file row |
| Select for deletion | Check the checkbox (original is always protected) |
| Delete | Click "Eliminar", type `CONFIRM` to confirm |

## Project structure

```
DupeCleaner/
├── index.html              # the entire app
├── GoogleSans-Regular.ttf  # optional — falls back to system sans-serif
├── GoogleSans-Bold.ttf     # optional — falls back to system sans-serif
└── README.md
```

## Deploy to GitHub Pages

1. Fork or clone this repo
2. Go to **Settings → Pages → Source: main / root**
3. Done — live at `https://<your-username>.github.io/DupeCleaner/`

## License

MIT — do whatever you want with it.

---

## 🇪🇸 Español

# 🔍 DupeCleaner

Buscador de archivos duplicados que funciona 100% en el navegador. Sin servidor, sin subidas — todo local. Selecciona una carpeta, la app escanea todos los archivos de forma recursiva con SHA-256, agrupa las copias idénticas por contenido y las muestra en tiempo real para que puedas revisarlas y eliminarlas sin salir del navegador.

---

## Características

- Pre-filtro por tamaño — archivos con distinto tamaño se descartan sin ninguna lectura de disco
- Muestreo inteligente — para archivos de más de 20 MB, solo lee tres fragmentos de 2 MB (inicio · centro · final), limitando el consumo a 6 MB de RAM sin importar el tamaño del archivo
- Web Worker inline — SHA-256 corre fuera del hilo principal, la interfaz no se congela en ningún momento
- Previsualización nativa — imágenes, texto, código, PDF, vídeo y audio
- Escaneo configurable — ignora carpetas de desarrollo, archivos ocultos, extensiones del sistema; define un tamaño mínimo
- Chips de filtro por formato — filtra los grupos de duplicados por extensión con un clic
- Tema oscuro / claro, guardado en `localStorage`
- Responsive — panel de feed plegable, botón flotante FAB, compatible con Android Chrome
- Firefox / Safari — solo escaneo (sin eliminación, limitación del navegador)
- Sin dependencias — un solo archivo `.html`, sin build, sin `npm install`

## Requisitos

Un navegador moderno. Chrome 86+ o Edge 86+ para funcionalidad completa (escaneo + eliminación). Firefox y Safari para escaneo únicamente.

## Ejecutar

Sin instalación. Abre `index.html` directamente en el navegador, o usa la versión en línea:

```
https://jaimefg1888.github.io/DupeCleaner/
```

### Controles

| Acción | Cómo |
|--------|------|
| Seleccionar carpeta | Clic en "Seleccionar carpeta" |
| Detener escaneo | Clic en "Detener" en la barra de navegación |
| Previsualizar archivo | Clic en el botón 👁 de cualquier fila |
| Seleccionar para borrar | Marcar el checkbox (el original siempre está protegido) |
| Eliminar | Clic en "Eliminar", escribe `CONFIRMAR` para confirmar |

## Estructura del proyecto

```
DupeCleaner/
├── index.html              # la aplicación completa
├── GoogleSans-Regular.ttf  # opcional — usa system sans-serif si no está
├── GoogleSans-Bold.ttf     # opcional — usa system sans-serif si no está
└── README.md
```

## Despliegue en GitHub Pages

1. Haz fork o clona este repositorio
2. Ve a **Settings → Pages → Source: main / root**
3. Listo — disponible en `https://<tu-usuario>.github.io/DupeCleaner/`

## Licencia

MIT — úsalo como quieras.
