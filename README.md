# DupeCleaner 🔍

**A browser-based duplicate file finder. No server, no uploads — 100% local.**

Select a folder, and DupeCleaner recursively scans all files using SHA-256 hashing to detect byte-for-byte identical copies. Results appear in real time. You can preview files, filter by format, and permanently delete duplicates — all without leaving the browser tab.

[![Live Demo](https://img.shields.io/badge/live-demo-ff0033?style=flat-square)](https://jaimefg1888.github.io/DupeCleaner/)
[![Chrome 86+](https://img.shields.io/badge/Chrome-86%2B-4285F4?style=flat-square&logo=googlechrome&logoColor=white)](https://www.google.com/chrome/)
[![Edge 86+](https://img.shields.io/badge/Edge-86%2B-0078D7?style=flat-square&logo=microsoftedge&logoColor=white)](https://www.microsoft.com/edge)

---

## How it works

1. The user picks a folder via the native OS directory picker
2. The app traverses all files recursively
3. **Phase 1 — size filter:** groups files by size (fast, no content read)
4. **Phase 2 — SHA-256:** computes exact hash only for same-size candidates
5. Duplicate groups appear in real time as they are detected
6. Each file can be previewed (images, text, code, PDFs) before deleting
7. The **original** (first file in each group) is always protected — it cannot be selected for deletion
8. Deletion requires typing `CONFIRMAR` / `CONFIRM` manually to confirm

---

## Tech stack

| Technology | Purpose |
|---|---|
| **File System Access API** | Read and delete local files (Chrome/Edge 86+) |
| **SubtleCrypto SHA-256** | Exact content comparison |
| **Plain HTML + JS** | Zero dependencies, no build step, no server needed |

---

## Browser compatibility

| Browser | Supported |
|---|---|
| Chrome 86+ | ✅ |
| Edge 86+ | ✅ |
| Firefox | ❌ (no File System Access API) |
| Safari | ❌ |

---

## Deploy to GitHub Pages

1. Create a repository named `DupeCleaner`
2. Upload these files:
   ```
   DupeCleaner/
   ├── index.html
   ├── GoogleSans-Regular.ttf
   ├── GoogleSans-Bold.ttf
   └── README.md
   ```
3. Go to **Settings → Pages → Source: main / root**
4. Your app will be live at: `https://jaimefg1888.github.io/DupeCleaner/`

> The `GoogleSans-Regular.ttf` and `GoogleSans-Bold.ttf` font files are required. Copy them from your portfolio repo.

---

---

# DupeCleaner 🔍

**Buscador de archivos duplicados que funciona 100% en el navegador. Sin servidor, sin subidas — todo local.**

Selecciona una carpeta y DupeCleaner escanea todos los archivos de forma recursiva usando SHA-256 para detectar copias exactas byte a byte. Los resultados aparecen en tiempo real. Puedes previsualizar archivos, filtrar por formato y eliminar duplicados permanentemente — sin salir del navegador.

---

## Cómo funciona

1. El usuario selecciona una carpeta con el selector nativo del sistema operativo
2. La app recorre todos los archivos de forma recursiva
3. **Fase 1 — filtro por tamaño:** agrupa por tamaño (rápido, sin leer contenido)
4. **Fase 2 — SHA-256:** calcula el hash exacto solo de los candidatos del paso anterior
5. Los grupos de duplicados aparecen en tiempo real a medida que se detectan
6. Cada archivo se puede previsualizar (imágenes, texto, código, PDFs) antes de eliminar
7. El **original** (primer archivo de cada grupo) está siempre protegido — no se puede seleccionar para borrar
8. La eliminación requiere escribir `CONFIRMAR` manualmente para confirmar

---

## Stack tecnológico

| Tecnología | Uso |
|---|---|
| **File System Access API** | Leer y eliminar archivos locales (Chrome/Edge 86+) |
| **SubtleCrypto SHA-256** | Comparación exacta de contenido |
| **HTML + JS puro** | Sin dependencias, sin build, sin servidor |

---

## Compatibilidad de navegadores

| Navegador | Compatible |
|---|---|
| Chrome 86+ | ✅ |
| Edge 86+ | ✅ |
| Firefox | ❌ (no soporta File System Access API) |
| Safari | ❌ |

---

## Despliegue en GitHub Pages

1. Crea un repositorio llamado `DupeCleaner`
2. Sube estos archivos:
   ```
   DupeCleaner/
   ├── index.html
   ├── GoogleSans-Regular.ttf
   ├── GoogleSans-Bold.ttf
   └── README.md
   ```
3. Ve a **Settings → Pages → Source: main / root**
4. Tu app estará en: `https://jaimefg1888.github.io/DupeCleaner/`

> Los ficheros `GoogleSans-Regular.ttf` y `GoogleSans-Bold.ttf` son necesarios. Cópialos desde tu repo de portfolio.
