# DupeCleaner 🔍

Buscador de archivos duplicados que corre 100% en el navegador.
No requiere servidor, no sube nada a internet. Todo local.

## Tecnología
- **File System Access API** (Chrome/Edge 86+) para leer y eliminar archivos
- **SubtleCrypto SHA-256** para comparación exacta de contenido
- **Sin dependencias de Python** — HTML + JS puro

## Despliegue en GitHub Pages

1. Crea un repositorio llamado `DupeCleaner`
2. Sube estos archivos:
   - `index.html`
   - `GoogleSans-Regular.ttf`
   - `GoogleSans-Bold.ttf`
3. Ve a Settings → Pages → Source: **main / root**
4. Tu app estará en: `https://jaimefg1888.github.io/DupeCleaner/`

## Archivos necesarios en el repo
```
DupeCleaner/
├── index.html
├── GoogleSans-Regular.ttf   ← copia desde tu portfolio
├── GoogleSans-Bold.ttf      ← copia desde tu portfolio
└── README.md
```

## Navegadores compatibles
| Navegador | Compatible |
|-----------|-----------|
| Chrome 86+ | ✅ |
| Edge 86+ | ✅ |
| Firefox | ❌ (no soporta File System Access API) |
| Safari | ❌ |

## Cómo funciona
1. El usuario selecciona una carpeta con el selector nativo del OS
2. La app recorre todos los archivos recursivamente
3. Fase 1: agrupa por tamaño (filtro rápido, sin leer contenido)
4. Fase 2: calcula SHA-256 solo de los candidatos del paso anterior
5. Muestra en tiempo real los grupos de duplicados
6. El usuario puede previsualizar cada archivo antes de borrar
7. El "original" (primer archivo de cada grupo) **nunca** se puede seleccionar para borrar
8. Para eliminar hay que escribir `CONFIRMAR` manualmente
