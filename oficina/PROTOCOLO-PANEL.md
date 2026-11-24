# Cómo informar al panel de la oficina

Cada agente, al terminar (o al terminar cada entrega importante), deja **una tarjeta por entrega** en el panel. El dueño solo mira el panel: si no está en el panel, no existe.

Panel: https://claude.ai/artifact/V3xEN4BoGpEmcp5S9KoRg4 · slug `e329682e-9a42-4a74-8d51-b71a934fbac9`

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
  "web": "aluacatering",              // levantehub | erevanprint | unicovalencia | aluacatering | fachadaslevante | todas
  "tipo": "reel",                     // guia | traduccion | curso | reel | short | video | post | resena | informe | herramienta | lead | oportunidad | seo
  "estado": "tu-ok",                  // hecho | tu-ok (espera revisión o que lo suba él) | trabajando | error
  "tarea": "Reel: menú de Navidad para empresas",   // título corto, máx. 70 caracteres
  "resumen": "Qué es y por qué, en 1-2 frases sencillas (máx. 200 caracteres).",
  "accion_tuya": "Subir a Instagram de ALUA a las 13:00",   // solo si el dueño tiene que hacer algo; si no, omítelo
  "enlaces": [{"t": "Descargar reel", "u": "https://..."}]  // solo https; 1-3 enlaces
}
```

Reglas:
- **Un vídeo = una tarjeta** con `tipo` `reel`, `short` o `video` y el enlace directo al .mp4 como **primer** enlace (el panel lo muestra como vídeo con ▶).
- Lenguaje de dueño de negocio, nada técnico. Sin markdown dentro de los textos.
- Si algo falla: tarjeta con `estado:"error"`, el motivo exacto en `resumen` y qué hacer en `accion_tuya`.
- No escribas en `dias/…`: eso es solo de Dirección.

## Si el panel no responde

Si `db_write` falla dos veces, guarda las mismas tarjetas como lista JSON en `oficina/estado/<AAAA-MM-DD>/<depto>.json` de este repo (commit y push). Dirección las sube al panel a las 9:07.
