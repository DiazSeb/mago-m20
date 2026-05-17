# El Eco de Athgealltanas — Crónica Web

Webpage estática para llevar la crónica de Mage: The Ascension M20.

## Cómo correrla

Desde esta carpeta, en la terminal:

```bash
python3 -m http.server 8000
```

Y abrir [http://localhost:8000](http://localhost:8000) en el navegador.

> No alcanza con abrir `index.html` directo (`file://` bloquea `fetch()` de los `.md`).

## Estructura

```
.
├── index.html                       # La app
├── manifest.json                    # Lista de secciones y sesiones
├── data/                            # El "canon" de la crónica
│   ├── inicio.md                    # Dashboard / estado actual
│   ├── personajes.md                # Adam · James · Mel
│   ├── magia.md                     # Rotes
│   ├── lugares.md                   # Athgealltanas + Doissetep
│   ├── aliados.md
│   ├── enemigos.md
│   ├── figuras.md                   # Vargas, Mallory, Gulliver, Cofradía
│   ├── amenazas.md                  # Marte-1, Criatura, Cometa
│   ├── lore.md                      # Heylel, Kentaro
│   ├── cronologia.md
│   └── quests.md                    # Quests + Misterios
├── sessions/
│   ├── _template.md                 # Plantilla para sesiones nuevas
│   └── session_N.md                 # (se va llenando sesión a sesión)
└── ElEcoDeAthgealltanas_BASE.md     # Backup del documento original
```

## Workflow después de cada sesión

1. Contale a Claude qué pasó en la sesión.
2. Claude:
   - Crea `sessions/session_N.md` con el log estructurado de la sesión
   - Actualiza los `data/*.md` que cambiaron (canon nuevo: NPCs, quests, estado del nodo, etc.)
   - Agrega la sesión al array `sessions` en `manifest.json`
3. Refrescá el navegador y la sesión aparece en el sidebar.

## Notas

- **Buscador:** la caja de búsqueda del sidebar rastrea texto en todos los archivos `.md` (mínimo 2 caracteres).
- **Atajos:** los hashes de URL funcionan — podés mandar `http://localhost:8000/#personajes` o `#quests`.
- **Tablas, citas, énfasis:** todo el GFM estándar está soportado vía `marked.js` (CDN).
- **Sin backend:** todo es estático. Si querés publicarla online, GitHub Pages o Netlify Drop funcionan tal cual.
