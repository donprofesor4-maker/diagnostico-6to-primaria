# Misión Diagnóstico 6.º Primaria · Informática

Quiz interactivo para el diagnóstico de Informática de 6.º de primaria (Colegio de
Cervantes). Los alumnos responden 30 reactivos (4 opciones A/B/C/D) en una página
divertida guiada por DonBOT 🤖 y obtienen su resultado al instante. Publicado en
GitHub Pages con el GitHub de Don Profesor (`donprofesor4-maker`).

Las respuestas se guardan en la **misma** hoja de Google del diagnóstico de 4.º
("Diagnóstico Informática 4to"), en la pestaña **`Respuestas 6to Prim`**. El de
4.º (pestaña `Respuestas`) y el de 2.º (pestaña `Respuestas 2do Sec`) no se tocan.

## Archivos

| Archivo | Descripción |
|---|---|
| `index.html` | Quiz autónomo (vanilla JS, sin dependencias; 30 reactivos con 4 opciones barajadas por intento) |
| `apps-script.gs` / `Code.gs` | Código de Google Apps Script (backend que rutea por `grado`: "4to" → `Respuestas`, "2do" → `Respuestas 2do Sec`, "6to" → `Respuestas 6to Prim`; crea la pestaña si no existe) |

## Página viva

- HTTPS: `https://donprofesor4-maker.github.io/diagnostico-6to-primaria/`

## Estado actual (conectado)

- Web app Apps Script: "Misión Diagnóstico 4to" — deployment activo (misma URL
  `/exec` compartida con 4.º y 2.º) apuntando a la **Versión 4** (código con ruteo
  por `grado`, incluido "6to"). El deployment se actualiza eligiendo **Nueva
  versión** sin cambiar el ID de implementación, así 4.º y 2.º siguen funcionado
  por la misma URL.
- Hoja: "Diagnóstico Informática 4to" → pestaña `Respuestas 6to Prim`.
- `SCRIPT_URL` en `index.html` apunta a la URL `/exec` compartida.

## Cómo conectar la hoja de respuestas (Google Sheets)

1. Abre [script.google.com](https://script.google.com), el proyecto "Misión Diagnóstico 4to"
   y pega el contenido de `apps-script.gs` en `Code.gs` (ya está el ruteo por `grado`).
2. El Google Sheet ("Diagnóstico Informática 4to") queda vinculado.
3. **Implementar > Administrar las implementaciones > Editar** del deployment activo:
   - **Ejecutar como:** Yo (tu cuenta)
   - **Acceso:** Cualquier usuario (incluso anónimo) — los alumnos no necesitan cuenta de Google.
   - Cambia **Versión** a **Nueva versión** y pulsa **Implementar**. El ID de
     implementación y la URL `/exec` no cambian, así los otros grados no se rompen.
4. Copia la URL que termina en `/exec` y, si hace falta, ajústala en `index.html`.

> Si `SCRIPT_URL` está vacía, el quiz igual funciona: el alumno descarga un
> respaldo `.json` y se lo entrega a la profe.

## Desplegar cambios

```bash
git add -A && git commit -m "..." && git push
```

GitHub Pages publica automáticamente desde la rama `main`.