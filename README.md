<div align="center">

<h1>
  <img src="https://img.shields.io/badge/dupe-cleaner-ff0033?style=flat-square&logoColor=white" alt="DupeCleaner" height="28">
</h1>

**Find and delete duplicate files — directly in your browser. No server. No uploads. Zero dependencies.**

[![Live Demo](https://img.shields.io/badge/▶_Live_Demo-ff0033?style=flat-square)](https://jaimefg1888.github.io/DupeCleaner/)
[![Vanilla JS](https://img.shields.io/badge/Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![No Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen?style=flat-square)](https://jaimefg1888.github.io/DupeCleaner/)
[![Single File](https://img.shields.io/badge/single_file-index.html-blue?style=flat-square)](./index.html)
[![License: MIT](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)](./LICENSE)
[![Chrome 86+](https://img.shields.io/badge/Chrome-86%2B-4285F4?style=flat-square&logo=googlechrome&logoColor=white)](https://www.google.com/chrome/)
[![Edge 86+](https://img.shields.io/badge/Edge-86%2B-0078D7?style=flat-square&logo=microsoftedge&logoColor=white)](https://www.microsoft.com/edge)

</div>

---

## What is it?

DupeCleaner is a **single HTML file** that turns your browser into a high-performance duplicate file detector. Pick a folder — the app recursively scans every file inside it using **SHA-256**, groups identical copies by content (not by name), and shows them in real time so you can review and purge them on the spot.

**Your files never leave your device.** There is no backend, no API call, no cloud sync. Everything — scanning, hashing, deleting — happens locally in your browser tab.

### Why is it fast and RAM-safe?

Most duplicate finders read entire files into memory to hash them. That crashes on a 20 GB video library. DupeCleaner uses two optimisations:

- **Size pre-filter** — files with different sizes cannot be identical. They are skipped before any I/O.
- **Smart sampling** — for files above 20 MB, it reads only three 2 MB slices (start · middle · end) via `File.slice()`, capped at **6 MB of RAM regardless of file size**. Hashing runs in a dedicated **Web Worker** so the UI stays responsive throughout.

---

## Killer features

| | Feature |
|---|---|
| 🔒 | **100% local & private** — nothing touches a server, ever |
| ⚡ | **Inline Web Worker** — SHA-256 off the main thread, UI never freezes |
| 🧠 | **RAM-safe sampling** — handles multi-GB files without OOM crashes |
| 🖥️ | **Multi-device** — desktop Chrome/Edge with full delete · Firefox/Safari for scan-only · Android Chrome supported |
| 🛡️ | **Smart OS exclusion** — automatically skips system paths on Windows, macOS and Linux |
| 👁️ | **Native preview** — images, text, code, PDF, video (`<video>`), audio (`<audio>`) |
| 🎛️ | **Configurable scan** — ignore dev folders, hidden files, system extensions; set a minimum file size |
| 🌑 | **Dark / Light theme** — persisted in `localStorage` |
| 📱 | **Responsive** — collapsible feed panel, floating FAB, mobile-first layout |
| 📦 | **Zero dependencies** — one `.html` file, no build step, no `npm install` |

---

## How it works

```
Pick folder
    │
    ▼
Phase 1 — collect all files, skip OS/dev/hidden paths
    │
    ▼
Phase 2 — group by file size  (fast, zero I/O)
    │
    ▼
Phase 3 — SHA-256 only for same-size candidates  →  Web Worker
    │         ≤ 20 MB: full read
    │          > 20 MB: 3 × 2 MB slices (start · mid · end)
    ▼
Duplicate groups render in real time as matches are found
    │
    ▼
Preview · filter by format · select · delete (Chrome/Edge only)
```

The **original** file in each group (the first encountered) is always protected and cannot be selected for deletion. Deleting requires typing `CONFIRM` / `CONFIRMAR` in the confirmation dialog.

---

## Usage

No installation. No npm. No CLI.

1. **Open the app →** [jaimefg1888.github.io/DupeCleaner](https://jaimefg1888.github.io/DupeCleaner/)
2. Click **"Seleccionar carpeta"** and pick any local folder
3. Watch the live feed as files are collected and hashed
4. Review the duplicate groups, preview files if needed, select the copies to remove
5. Click **Eliminar**, type the confirmation word, and they're gone

> **Tip — Chrome blocks root-level folders** (Downloads, Desktop) as a security measure. If you get an OS-level error, create a subfolder inside the target directory and select that instead.

> **Deletion requires Chrome or Edge (desktop or Android).** Firefox and Safari can scan and detect duplicates but cannot delete files from the web.

---

## Settings

Click the ⚙ gear icon in the nav bar to open the scan options panel:

| Option | Default | Description |
|---|---|---|
| Ignore dev folders | ✅ On | Skips `node_modules`, `.git`, `.cache`, `dist`, `__pycache__` and more |
| Ignore hidden folders | Off | Skips any folder whose name starts with `.` |
| Ignore system files | Off | Skips `.ini`, `.sys`, `.dll`, `.lnk`, `.bat` and related extensions |
| Min file size | 0 KB | Files smaller than this threshold are skipped entirely |
| Large file accuracy | Fast Mode | Sampling (start·mid·end) — ideal for video libraries. Switch to Thorough for byte-perfect precision at the cost of speed |

---

## Browser compatibility

| Browser | Scan | Delete |
|---|---|---|
| Chrome 86+ | ✅ | ✅ |
| Edge 86+ | ✅ | ✅ |
| Android Chrome | ✅ | ✅ |
| Firefox | ✅ *(fallback mode)* | ❌ |
| Safari | ✅ *(fallback mode)* | ❌ |

---

## Tech stack

| Technology | Role |
|---|---|
| **File System Access API** | Native folder picker + file deletion (Chrome/Edge) |
| **SubtleCrypto** | SHA-256 hashing in the browser, no library needed |
| **Web Worker (Blob URL)** | Hashing off the main thread — UI stays at 60 fps |
| **`File.slice()`** | RAM-safe chunked reads for large files |
| **`URL.createObjectURL()`** | Stream video/audio previews without copying to JS heap |
| **`<input webkitdirectory>`** | Fallback folder traversal for Firefox/Safari |

---

## Deploy your own copy

```
your-repo/
├── index.html           ← the entire app
├── GoogleSans-Regular.ttf
├── GoogleSans-Bold.ttf
└── README.md
```

1. Fork or clone this repo
2. Add the two `GoogleSans` font files (copy from your portfolio repo)
3. Go to **Settings → Pages → Source: main / root**
4. Done — live at `https://<your-username>.github.io/<repo-name>/`

No server required. The `index.html` is fully self-contained.

---

## License

MIT — do whatever you want with it.

---

---

<div align="center">

**· · ·**

</div>

---

---

## ¿Qué es?

DupeCleaner es un **único archivo HTML** que convierte tu navegador en un detector de archivos duplicados de alto rendimiento. Selecciona una carpeta — la app recorre todos los archivos de forma recursiva usando **SHA-256**, agrupa las copias idénticas por contenido (no por nombre) y las muestra en tiempo real para que puedas revisarlas y eliminarlas sin salir del navegador.

**Tus archivos nunca salen de tu dispositivo.** No hay backend, ni llamadas a API, ni sincronización en la nube. Todo — escaneo, hasheo, eliminación — ocurre localmente en tu pestaña del navegador.

### ¿Por qué es rápido y seguro para la RAM?

La mayoría de buscadores de duplicados leen los archivos enteros en memoria para hashearlos. Eso colapsa con una librería de vídeos de 20 GB. DupeCleaner usa dos optimizaciones:

- **Pre-filtro por tamaño** — si dos archivos tienen tamaños diferentes, no pueden ser idénticos. Se descartan sin hacer ninguna lectura de disco.
- **Muestreo inteligente** — para archivos de más de 20 MB, solo lee tres fragmentos de 2 MB (inicio · centro · final) mediante `File.slice()`, limitando el consumo a **6 MB de RAM sin importar el tamaño del archivo**. El hasheo corre en un **Web Worker** dedicado para que la interfaz permanezca fluida en todo momento.

---

## Características principales

| | Característica |
|---|---|
| 🔒 | **100% local y privado** — nada toca un servidor, jamás |
| ⚡ | **Web Worker inline** — SHA-256 fuera del hilo principal, la UI no se congela |
| 🧠 | **Muestreo seguro para la RAM** — maneja archivos de varios GB sin crashes por OOM |
| 🖥️ | **Multidispositivo** — Chrome/Edge con eliminación completa · Firefox/Safari en modo solo lectura · Android Chrome compatible |
| 🛡️ | **Exclusión inteligente de rutas del SO** — omite automáticamente las carpetas del sistema en Windows, macOS y Linux |
| 👁️ | **Previsualización nativa** — imágenes, texto, código, PDF, vídeo (`<video>`), audio (`<audio>`) |
| 🎛️ | **Escaneo configurable** — ignora carpetas de desarrollo, archivos ocultos, extensiones del sistema; define un tamaño mínimo |
| 🌑 | **Tema oscuro / claro** — guardado en `localStorage` |
| 📱 | **Diseño responsive** — panel de feed plegable, botón flotante FAB, layout mobile-first |
| 📦 | **Sin dependencias** — un solo archivo `.html`, sin build, sin `npm install` |

---

## Cómo funciona

```
Seleccionar carpeta
    │
    ▼
Fase 1 — recopilar archivos, omitir rutas del SO / desarrollo / ocultos
    │
    ▼
Fase 2 — agrupar por tamaño  (instantáneo, sin leer disco)
    │
    ▼
Fase 3 — SHA-256 solo para candidatos del mismo tamaño  →  Web Worker
    │         ≤ 20 MB: lectura completa
    │          > 20 MB: 3 × 2 MB (inicio · centro · final)
    ▼
Los grupos de duplicados aparecen en tiempo real según se detectan
    │
    ▼
Previsualizar · filtrar por formato · seleccionar · eliminar (solo Chrome/Edge)
```

El archivo **original** de cada grupo (el primero en encontrarse) siempre está protegido y no puede seleccionarse para eliminar. La eliminación requiere escribir `CONFIRMAR` en el diálogo de confirmación.

---

## Uso

Sin instalación. Sin npm. Sin CLI.

1. **Abre la app →** [jaimefg1888.github.io/DupeCleaner](https://jaimefg1888.github.io/DupeCleaner/)
2. Haz clic en **"Seleccionar carpeta"** y elige cualquier carpeta local
3. Observa el registro en vivo mientras se recopilan y hashean los archivos
4. Revisa los grupos de duplicados, previsualiza si lo necesitas, selecciona las copias a eliminar
5. Pulsa **Eliminar**, escribe la palabra de confirmación y listo

> **Aviso — Chrome bloquea carpetas raíz** (Descargas, Escritorio) por seguridad. Si recibes un error del sistema operativo, crea una subcarpeta dentro del directorio objetivo y selecciónala en su lugar.

> **La eliminación requiere Chrome o Edge (escritorio o Android).** Firefox y Safari pueden escanear y detectar duplicados pero no pueden borrar archivos desde la web.

---

## Configuración

Haz clic en el icono ⚙ de la barra de navegación para abrir el panel de opciones:

| Opción | Por defecto | Descripción |
|---|---|---|
| Ignorar carpetas de desarrollo | ✅ Sí | Omite `node_modules`, `.git`, `.cache`, `dist`, `__pycache__` y más |
| Ignorar carpetas ocultas | No | Omite cualquier carpeta cuyo nombre empiece por `.` |
| Ignorar archivos del sistema | No | Omite `.ini`, `.sys`, `.dll`, `.lnk`, `.bat` y extensiones similares |
| Tamaño mínimo de archivo | 0 KB | Archivos más pequeños que este umbral se ignoran por completo |
| Precisión en archivos gigantes | Modo Rápido | Muestreo (inicio·centro·final) — ideal para librerías de vídeo. Cambia a Exhaustivo para precisión byte a byte |

---

## Compatibilidad de navegadores

| Navegador | Escaneo | Eliminación |
|---|---|---|
| Chrome 86+ | ✅ | ✅ |
| Edge 86+ | ✅ | ✅ |
| Android Chrome | ✅ | ✅ |
| Firefox | ✅ *(modo alternativo)* | ❌ |
| Safari | ✅ *(modo alternativo)* | ❌ |

---

## Stack tecnológico

| Tecnología | Función |
|---|---|
| **File System Access API** | Selector de carpeta nativo + eliminación de archivos (Chrome/Edge) |
| **SubtleCrypto** | SHA-256 en el navegador, sin librerías externas |
| **Web Worker (Blob URL)** | Hasheo fuera del hilo principal — la UI se mantiene a 60 fps |
| **`File.slice()`** | Lecturas por fragmentos seguras para la RAM en archivos grandes |
| **`URL.createObjectURL()`** | Previsualización de vídeo/audio en streaming sin copiar a heap de JS |
| **`<input webkitdirectory>`** | Recorrido de carpetas alternativo para Firefox/Safari |

---

## Despliegue propio

```
tu-repo/
├── index.html           ← la aplicación completa
├── GoogleSans-Regular.ttf
├── GoogleSans-Bold.ttf
└── README.md
```

1. Haz fork o clona este repositorio
2. Añade los dos ficheros de fuente `GoogleSans` (cópialos desde tu repo de portfolio)
3. Ve a **Settings → Pages → Source: main / root**
4. Listo — disponible en `https://<tu-usuario>.github.io/<nombre-repo>/`

No necesitas servidor. El `index.html` es completamente autocontenido.

---

## Licencia

MIT — úsalo como quieras.
