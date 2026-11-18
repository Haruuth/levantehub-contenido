# Guía editorial de LevanteHUB

Cada guía es un archivo `guias/<slug>.json`. La web (levantehub.es) los lee y los publica sola.

## Esquema
```json
{
  "slug": "kebab-case-sin-tildes",
  "title": "Título claro (máx. ~65 caracteres)",
  "description": "Meta descripción 140-160 caracteres",
  "intro": "Párrafo de entrada",
  "department": "google-business | academia | servicios-web",
  "date": "YYYY-MM-DD",
  "tags": ["..."],
  "body": [
    {"type":"h2","text":"..."},
    {"type":"p","text":"..."},
    {"type":"list","items":["..."]},
    {"type":"checklist","items":["..."]},
    {"type":"tip","text":"..."},
    {"type":"answer","text":"..."}
  ],
  "faq": [{"q":"...","a":"..."}]
}
```
(Ajustar a los tipos reales de `src/content/types.ts` si difieren.)

## Método de investigación diaria
1. Buscar qué preguntan negocios locales de Valencia/España sobre ficha de Google, SEO local, web y medición.
2. Revisar guías existentes en `guias/` para no repetir tema.
3. Elegir una consulta real con intención clara; responderla de forma práctica.

## Reglas de calidad
- Español de España, tono cercano y concreto, sin relleno.
- Mínimo 900 palabras útiles, pasos accionables, ejemplos de negocios locales.
- Nada de datos inventados, cifras sin fuente ni garantías de resultados.
- Citar la fuente oficial (Google, etc.) cuando se afirme algo técnico.
- 1 guía al día, un único archivo JSON válido por guía.
