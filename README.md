# Atelier Romance — Sitio web

> *No organizamos bodas. Diseñamos patrimonios experienciales que duran cuatro días y se recuerdan toda la vida.*

Sitio de propuesta para **Atelier Romance** — couture destination weddings *by Barichara Travel* (Barichara, Santander, Colombia).

Tres pantallas conectadas, en español (con toggle ES/EN en la experiencia de novios).

---

## 🌐 Ver el sitio

- **Punto de entrada:** [`Atelier Romance Entrada.dc.html`](Atelier%20Romance%20Entrada.dc.html) — pantalla de selección **Novios / Wedding Planner**.
- El archivo [`index.html`](index.html) redirige automáticamente a esa pantalla (útil para GitHub Pages).

### Publicar en GitHub Pages
1. Sube este repositorio a GitHub.
2. **Settings → Pages → Source: `main` / root.**
3. En unos minutos el sitio queda en línea en `https://<usuario>.github.io/<repo>/`.
   Gracias a `index.html`, abre directo en la pantalla de entrada.

---

## 📄 Estructura

| Archivo | Qué es | Enlaza a |
|---|---|---|
| `index.html` | Redirección automática al punto de entrada (para Pages). | → Entrada |
| `Atelier Romance Entrada.dc.html` | **Punto de entrada.** Selección Novios / Soy Wedding Planner. | → Ternura · Final |
| `Atelier Romance Ternura.dc.html` | Experiencia de **novios**: manifiesto, 4 actos, formatos, paleta, app, galería, agenda tu cita. | — |
| `Atelier Final.dc.html` | Programa **Pro / Wedding Planners**: servicios marca blanca, paquetes, fotografía, contacto. | — |

### Carpetas y apoyos
| Ruta | Contenido |
|---|---|
| `assets/photos/` | Fotografías del sitio. |
| `assets/stickers/` | Stickers decorativos (flores, mariposas, faroles…). |
| `assets/favicon.png` | Ícono del sitio. |
| `brand/` | Emblemas y logotipo de Atelier Romance. |
| `support.js` | Runtime que hace funcionar los archivos `.dc.html`. **No editar.** |
| `image-slot.js` | Componente auxiliar de imágenes. |

---

## 💻 Correr en local (VS Code)

Los `.dc.html` usan `fetch` interno, así que **no se abren con doble clic** — necesitan un servidor local:

**Opción A — Extensión Live Server (más fácil)**
- Instala **Live Server** (Ritwick Dey) en VS Code.
- Clic derecho en `index.html` → **Open with Live Server**.

**Opción B — Python**
```bash
python3 -m http.server 8000
# luego abre http://localhost:8000
```

**Opción C — Node**
```bash
npx serve .
```

---

## 📨 Formulario "Agenda tu cita" → Google Sheets

El formulario de la página de **novios** envía cada respuesta a una Google Sheet mediante un **Google Apps Script** publicado como aplicación web.

- La URL del script está en `Atelier Romance Ternura.dc.html`, dentro de la función `submitForm` (constante `SHEET_ENDPOINT`).
- El paso a paso para crear/cambiar ese puente está en [`CONECTAR-GOOGLE-SHEET.md`](CONECTAR-GOOGLE-SHEET.md).
- Cada envío crea una fila con: *fecha de envío, pareja, correo, fecha tentativa, destino, historia, idioma, origen.*

> ⚠️ La URL del Apps Script es pública por diseño (recibe los envíos). Si en algún momento quieres rotarla, vuelve a desplegar el script y actualiza `SHEET_ENDPOINT`.

### Agendar llamada (Wedding Planners)
Los botones **AGENDAR** del portafolio abren un calendario de **Cal.com**:
`https://cal.com/atelieromance.bybaricharatravel/hagamos-equipo`

---

## 🎨 Sistema de diseño

**Tipografías** (Google Fonts, ya enlazadas):
- `Cormorant Garamond` — titulares (serif editorial)
- `Jost` — cuerpo / UI
- `Pinyon Script` — acentos caligráficos

**Paleta:**
| Color | Hex |
|---|---|
| Crema fondo | `#F5EFE4` |
| Tinta / texto | `#1C1813` · `#241c14` |
| Dorado Atelier | `#C7A052` · `#A67C2E` · `#D8B86A` |
| Terracota | `#9E5A3C` |
| Verde laurel (paquete Dúo) | degradado `#e6efd8 → #d6e6bf → #eef4e6` |

---

## ✏️ Editar

Cada `.dc.html` es autónomo y contiene tres bloques: el **template** (HTML visible), la **lógica** (`class Component extends DCLogic`) y los **textos** ES/EN (objeto de traducciones dentro de la lógica). Las fotos se referencian como `assets/photos/<nombre>.jpg`.

---

## 📌 Notas
- Requiere conexión a internet la primera vez para cargar las fuentes de Google Fonts.
- Los `.dc.html` son diseños de alta fidelidad en HTML; reflejan el look & feel y el comportamiento final.

---

© 2026 Atelier Romance · by Barichara Travel
