# Atelier Romance — Sitio web (propuesta)

Sitio de propuesta para **Atelier Romance** (couture destination weddings, Barichara).
Tres pantallas conectadas, en español (con toggle ES/EN en la experiencia de novios).

---

## 🚀 Cómo abrirlo en Visual Studio Code

1. **Abre la carpeta** completa en VS Code (`File → Open Folder…`).
2. Estos archivos **no se abren con doble clic** (usan `fetch` interno, que el navegador bloquea desde `file://`). Necesitas un servidor local — cualquiera de estas opciones:

   **Opción A — Extensión Live Server (la más fácil)**
   - Instala la extensión **Live Server** (Ritwick Dey) desde el panel de Extensiones.
   - Clic derecho sobre `Atelier Romance Entrada.dc.html` → **Open with Live Server**.

   **Opción B — Terminal (si tienes Python)**
   ```bash
   python3 -m http.server 8000
   ```
   Luego abre en el navegador: `http://localhost:8000/Atelier%20Romance%20Entrada.dc.html`

   **Opción C — Terminal (si tienes Node)**
   ```bash
   npx serve .
   ```

3. **Empieza siempre por `Atelier Romance Entrada.dc.html`** — es el punto de entrada (la pantalla de selección Novios / Wedding Planner).

---

## 📄 Estructura de las pantallas

| Archivo | Qué es | Enlaza a |
|---|---|---|
| `Atelier Romance Entrada.dc.html` | **Punto de entrada.** Pantalla de selección: Novios / Soy Wedding Planner. | → Ternura y Final |
| `Atelier Romance Ternura.dc.html` | Experiencia de **novios** (la propuesta emocional, formatos, paleta, app, galería). | — |
| `Atelier Final.dc.html` | Programa **Pro / Wedding Planners** (servicios marca blanca, paquetes, fotografía). | — |

### Archivos de apoyo
- `support.js` — runtime que hace funcionar los `.dc.html`. **No editar.** Debe quedar junto a los HTML.
- `image-slot.js` — componente auxiliar de imágenes.
- `assets/` — fotos (`assets/photos/`) y stickers decorativos (`assets/stickers/`).
- `brand/` — emblemas y logotipo de Atelier Romance.

---

## ✏️ Cómo editar

Cada `.dc.html` es autónomo y contiene **tres bloques** dentro del archivo:
- El **template** (el HTML visible, dentro de `<x-dc>…</x-dc>`).
- La **lógica** (`class Component extends DCLogic { … }`, dentro de un `<script>`).
- Los **textos** ES/EN viven en la lógica, en el objeto de traducciones (`es:` / `en:`).

Para cambiar copys, fotos o colores normalmente basta con buscar el texto/valor dentro del archivo correspondiente. Las fotos se referencian como `assets/photos/<nombre>.jpg`.

---

## 🎨 Sistema de diseño (referencia rápida)

**Tipografías** (Google Fonts, ya enlazadas en cada archivo):
- `Cormorant Garamond` — titulares (serif editorial)
- `Jost` — cuerpo de texto / UI
- `Pinyon Script` — acentos caligráficos

**Colores principales:**
- Fondo crema `#F5EFE4`
- Tinta / texto `#1C1813` · `#241c14`
- Dorado Atelier `#C7A052` · `#A67C2E` · `#D8B86A`
- Terracota `#9E5A3C`
- Verde laurel (paquete Dúo) degradado `#e6efd8 → #d6e6bf → #eef4e6`

---

## ⚠️ Notas
- Los archivos `.dc.html` son **diseños de referencia en HTML** (prototipos de alta fidelidad). Reflejan el look & feel y el comportamiento final; si se van a integrar en otro entorno (un CMS, React, etc.), úsense como guía visual exacta.
- Requiere conexión a internet la primera vez para cargar las fuentes de Google Fonts.
