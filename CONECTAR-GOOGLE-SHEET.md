# Conectar el formulario de novios a tu Google Sheet

El formulario de **"Agenda tu cita"** (página de Novios) ya está listo para enviar las respuestas a tu hoja de cálculo. Solo falta crear el "puente" gratuito de Google (una vez) y pegar una URL.

Tu hoja:
https://docs.google.com/spreadsheets/d/1O4eCCa3Gw2AQqtYbZ6VAiaKxN8bHsvOxZeXNVdpE3xg/edit

---

## Paso 1 — Abre el editor de Apps Script
1. Abre tu Google Sheet.
2. Menú **Extensiones → Apps Script**.
3. Borra el código que aparezca y pega **todo** esto:

```javascript
function doPost(e) {
  var hoja = SpreadsheetApp.getActiveSpreadsheet().getSheets()[0];

  // Si la hoja está vacía, escribe los encabezados la primera vez
  if (hoja.getLastRow() === 0) {
    hoja.appendRow(['Fecha de envío','Pareja','Correo','Fecha tentativa','Destino','Historia','Idioma','Origen']);
  }

  var p = e.parameter;
  hoja.appendRow([
    new Date(),
    p.nombre  || '',
    p.correo  || '',
    p.fecha   || '',
    p.destino || '',
    p.mensaje || '',
    p.idioma  || '',
    p.origen  || ''
  ]);

  return ContentService.createTextOutput('OK');
}
```

4. Guarda (ícono del disquete o Ctrl/Cmd + S).

---

## Paso 2 — Publica el script como aplicación web
1. Arriba a la derecha: botón azul **Implementar → Nueva implementación**.
2. En el engranaje ⚙️ (Selecciona el tipo) elige **Aplicación web**.
3. Configura así:
   - **Descripción:** Formulario Atelier Romance (lo que quieras)
   - **Ejecutar como:** Yo (tu correo)
   - **Quién tiene acceso:** **Cualquier usuario** ← importante
4. Clic en **Implementar**.
5. Google te pedirá **autorizar** → acepta con tu cuenta (si sale "Google no verificó la app", entra en *Configuración avanzada → Ir a (nombre) → Permitir*).
6. Copia la **URL de la aplicación web** que aparece. Termina en **`/exec`**.

---

## Paso 3 — Pégame la URL (o pégala tú)
En el archivo **`Atelier Romance Ternura.dc.html`**, busca esta línea (dentro de `submitForm`):

```javascript
const SHEET_ENDPOINT = '';
```

Pon tu URL entre las comillas, por ejemplo:

```javascript
const SHEET_ENDPOINT = 'https://script.google.com/macros/s/AKfyc.../exec';
```

¡Listo! Cada vez que alguien envíe el formulario, aparecerá una fila nueva en tu hoja con fecha, pareja, correo, fecha tentativa, destino, historia, idioma y origen.

> Si me pasas la URL por el chat, yo la pego por ti y verifico que quede funcionando.

---

### Notas
- Si cambias el script más adelante, vuelve a **Implementar → Gestionar implementaciones → editar → Nueva versión** para que tome los cambios.
- La hoja guarda todo automáticamente; no se envían correos. Si además quieres aviso por correo, se puede agregar al script — dímelo.
