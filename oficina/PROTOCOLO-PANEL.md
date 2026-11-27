# Cómo informar al panel de la oficina

Cada agente, al terminar (o al terminar cada entrega importante), deja **una tarjeta por entrega** en el panel. El dueño solo mira el panel: si no está en el panel, no existe.

Panel: https://claude.ai/artifact/V3xEN4BoGpEmcp5S9KoRg4 · slug `e329682e-9a42-4a74-8d51-b71a934fbac9`

## PASO 0 (obligatorio, ANTES de empezar): tus tareas programadas

El dueño asigna, edita y borra tareas a cada trabajador desde el panel. Antes de hacer nada:

1. Carga `mcp__claude-artifacts__db_get` y lee `equipo/<agente>` del artefacto `e329682e-9a42-4a74-8d51-b71a934fbac9` para **cada** agente que representas (tabla de abajo). Si no existe, no hay cambios.
   **Nombres e ids:** cada trabajador tiene un id igual a su nombre (Laurik → `laurik`). Si el documento que lees tiene `renombrado_a`, el dueño le cambió el nombre: sigue a `equipo/<renombrado_a>` (puede haber varios saltos) y usa ESE id en todo, también en el campo `agente` de tus tarjetas. El campo `antes_ids` guarda los 2 nombres e ids anteriores, solo como historial para recuperar; no los uses.
2. `despedido: true` → ese agente está despedido: no hagas NADA de su trabajo (si representas a varios, haz solo el de los demás).
3. `principal_activa: false` → NO hagas tu trabajo principal de siempre; haz solo las tareas programadas. Si `principal` tiene texto, esa es la versión que manda el dueño de tu trabajo principal.
3. Para cada elemento de `tareas` con `activa: true`:
   - `cuando: "siempre"` → hazla en cada ejecución.
   - `cuando: "una"` → hazla solo si no tiene `hecha`; al terminar, márcala: `db_get` del documento, y `update` con `ifVersion` reescribiendo el array `tareas` igual pero con `"hecha": "AAAA-MM-DD"` en esa tarea.
   - Deja una tarjeta por cada tarea hecha con `"tarea_id": "<id de la tarea>"` y `"agente"`: así sale en su historial.
4. Si una tarea no se puede hacer (falta acceso, es ambigua o requiere pagar), tarjeta `estado:"error"` con el motivo y `tarea_id`.

| Tarea programada | Agentes que representa |
|---|---|
| LevanteHUB · Día completo (6:03) | clara, ivan-mila, leo |
| Curso gratis semanal (lunes) | teo |
| Oficina · Marketing clientes | sara |
| Oficina · Google Business | lucia |
| Oficina · Herramientas gratis | pau |
| Oficina · Oportunidades | bea |
| Oficina · Dirección · Resumen de Susanna (9:07) | susanna |
| [NUBE] Las 5 webs · Informe semanal | marta |
| [NUBE] LevanteHUB presencia online | alex |
| SEO semanal Fachadas Levante | jordi |
| Oficina · Captación · Raúl (leads 7:34) | raul |
| Oficina · Secretaría · Laurik (correo, PC de casa 8:43) | laurik |

## Herramienta

Usa `mcp__claude-artifacts__db_write` (si está diferida, cárgala con ToolSearch `select:mcp__claude-artifacts__db_write,mcp__claude-artifacts__db_get,mcp__claude-artifacts__db_query`). Un `db_write` cada vez, con todas las tarjetas del agente en `ops` (máx. 50).

- Tarjeta nueva: `{"op":"set","path":"tareas/<AAAA-MM-DD>_<depto>_<corto>","data":{...}}` sin `ifVersion`.
- Si el documento ya existe (por ejemplo, actualizar de `trabajando` a `hecho`): léelo antes con `db_get` y usa `{"op":"update", ..., "ifVersion": <versión>}`.

## Formato de la tarjeta (`data`)

```json
{
  "fecha": "2026-11-25",              // día de Madrid, obligatorio
  "hora": "07:52",                    // hora de Madrid al terminar
  "depto": "marketing",               // direccion | contenido | marketing | google | seo | herramientas | captacion | oportunidades
  "agente": "sara",                   // quién lo hizo (ver lista abajo); el panel coloca la tarjeta en su mesa
  "web": "aluacatering",              // levantehub | erevanprint | unicovalencia | aluacatering | fachadaslevante | todas
  "tipo": "reel",                     // guia | traduccion | curso | reel | short | video | post | resena | informe | herramienta | lead | oportunidad | seo
  "estado": "tu-ok",                  // hecho | tu-ok (espera revisión o que lo suba él) | trabajando | error
  "tarea": "Reel: menú de Navidad para empresas",   // título corto, máx. 70 caracteres
  "resumen": "Qué es y por qué, en 1-2 frases sencillas (máx. 200 caracteres).",
  "accion_tuya": "Subir a Instagram de ALUA a las 13:00",   // solo si el dueño tiene que hacer algo; si no, omítelo
  "enlaces": [{"t": "Descargar reel", "u": "https://..."}]  // solo https; 1-3 enlaces
}
```

Valores de `agente`: susanna, laurik, mher (sede) · clara, monica-y-mila, dr-joan, leo, sara (Nuri) · marta, alex, bea (Lumen) · nico, jordi, pau (Tuerca) · lucia, elena, raul (Rumbo).

## Vídeos e imágenes: que se vean DENTRO del panel (obligatorio)

El dueño y Susanna revisan reels, Shorts, posts y stories en el reproductor del panel, sin descargar nada. Para cada vídeo (.mp4) o imagen (.jpg/.png) que entregues:
1. Súbelo al panel con `mcp__claude-artifacts__upload_asset` (cárgala con ToolSearch): `slug` del panel y `files: [{"name": "AAAA-MM-DD-<web>-reel.mp4", "path": "<ruta local>"}]`. Máx. 32 MiB por archivo y 10 por llamada. Si te pide `shared_live`, repite la llamada con `"shared_live": "users"`.
2. Añade a la tarjeta el campo `"media": [{"tipo": "video"|"imagen", "url": "<url /_blob/... que devuelve>", "t": "Reel" | "Post 1" | "Story 1"...}]`. Máximo 8 elementos por tarjeta (el vídeo primero).
3. Mantén también el enlace al LEEME para copiar los textos.

Reglas:
- **Un vídeo = una tarjeta** con `tipo` `reel`, `short` o `video` y el enlace directo al .mp4 como **primer** enlace (el panel lo muestra como vídeo con ▶).
- Lenguaje de dueño de negocio, nada técnico. Sin markdown dentro de los textos.
- Si algo falla: tarjeta con `estado:"error"`, el motivo exacto en `resumen` y qué hacer en `accion_tuya`.
- No escribas en `dias/…`: eso es solo de Dirección.

## Accesos directos en cada tarjeta (obligatorio)

El dueño abre cada tarjeta y tiene que poder ver TODO lo que has hecho sin buscar. En `enlaces` pon un enlace por cada cosa que hayas creado, con un nombre claro (`t`) y la URL pública real (`u`, siempre https):

- Pieza publicada en la web: la URL española y, en la tarjeta de traducciones, la inglesa y la rusa.
- Vídeos: la copia en raw.githubusercontent.com del .mp4 (además del asset en `media`).
- Documento de textos (LEEME) en github.com.
- Informes, hojas de leads, oportunidades, PR: su enlace directo.

Traducciones: la URL usa el slug TRADUCIDO, el campo `slug` de `traducciones/<en|ru>/<slug_es>.json`, nunca el español. Rutas: `/en/guides/<slug>` o `/en/radar/<slug>`, `/ru/rukovodstva/<slug>` o `/ru/radar/<slug>`. Un 200 no basta: la web devuelve la portada con 200 cuando la ruta no existe. Comprueba con WebFetch que el título de la página es el del artículo; si sale la portada, la tarjeta va con `estado:"error"` y el motivo.

Textos para redes (campo `publicar`): uno por plataforma, adaptado y optimizado para su buscador: Instagram con gancho en la primera línea, palabras clave en el texto y máx. 5 hashtags; YouTube con título de 70 caracteres máximo con la palabra clave al principio y descripción con enlace y #Shorts; TikTok con texto corto y 3-5 hashtags si se publica allí.

## Reels, Shorts y posts que el director sube a mano: campo `publicar` (obligatorio)

Toda tarjeta con `estado: "tu-ok"` que haya que subir a una red lleva un campo `publicar`: una entrada por cada sitio donde va. El panel enseña el vídeo, un botón para descargarlo, el texto listo para copiar y un botón «Ya publicado aquí». Cuando el director marca todos, la tarjeta pasa sola a `hecho`.

```json
"publicar": [
  {"red": "instagram", "tipo": "Reel", "cuenta": "LevanteHUB", "texto": "Texto completo con emojis, enlace y hashtags"},
  {"red": "youtube", "tipo": "Short", "cuenta": "LevanteHUB", "titulo": "Título del Short", "texto": "Descripción con enlace y #Shorts"}
]
```

- `red`: `instagram`, `youtube`, `tiktok`, `facebook` o `google` (ficha de Google).
- `cuenta`: el nombre de la cuenta donde va (LevanteHUB, ALUA Catering, Único Valencia, Erevan Print, Fachadas Levante).
- `texto` (y `titulo` en YouTube): el texto final, completo, en español, para copiar y pegar tal cual. No pongas «ver LEEME».
- No hace falta hora: el director publica cuando puede.
- El vídeo tiene que estar subido como asset y puesto en `media` (sección anterior).
- `accion_tuya`: una frase corta, por ejemplo «Subir el reel a Instagram de LevanteHUB».

## ALUA Catering y ÚNICO Valencia: revisión de Susi (obligatorio)

Susi revisa todo lo que se va a publicar en **aluacatering** y **unicovalencia** desde la pestaña «Revisión de Susi» del panel. Ella **no lee español**: lee ruso o armenio. Por eso, en toda tarjeta con `web` = `aluacatering` o `unicovalencia` que lleve algo para publicar (reel, short, post, texto de web, publicación de ficha):

- `"texto"`: el texto EXACTO que se publicará, en español (caption del post, texto de la ficha, título y meta...). Máx. 1.500 caracteres. Las publicaciones siempre van en español.
- `"traduccion"`: `{"ru": "...", "hy": "..."}` con la traducción fiel al ruso y al armenio de `tarea` + `texto` (y del guion de voz si es un vídeo), para que entienda qué se publica. Lenguaje sencillo.
- `estado: "tu-ok"`.

Su respuesta queda en la colección `revisiones/<id de la tarjeta>` (`{"estado":"ok"|"cambios","nota"}`). Antes de preparar algo nuevo para esas dos webs, lee las revisiones de los últimos 7 días con `db_list` y aplica lo que pidió en `nota`.

## Si el panel no responde

Si `db_write` falla dos veces, guarda las mismas tarjetas como lista JSON en `oficina/estado/<AAAA-MM-DD>/<depto>.json` de este repo (commit y push). Dirección las sube al panel a las 9:07.
