# CURSOS GRATIS SEMANALES (cada lunes)

Un curso nuevo, gratuito y público cada lunes, en `cursos/AAAA-MM-DD_slug.json`. La web los lee de `contenido/cursos/` y publica `/cursos/<slug>` (rama `cursos-gratis` del repo web hasta que se fusione).

## Cómo se elige el tema (obligatorio)
1. Buscar con Windsor/Supermetrics (Search Console), Google Trends y las preguntas reales de la gente (WebSearch, "la gente también pregunta") una **búsqueda real y frecuente** del nicho (SEO, SEM, GEO/IA, Google Business, web para negocios locales) que resuelva un problema concreto.
2. No repetir temas: mirar `cursos/` y `guias/`.
3. Guardar la búsqueda elegida en el campo `busqueda`.

## Estudio previo OBLIGATORIO (un curso se posiciona si es el mejor resultado sobre el tema)
1. SERP: busca la `busqueda` en Google (WebSearch) y analiza los 5-8 primeros resultados: qué cubren, qué les falta, qué errores o datos desactualizados tienen. El curso debe cubrir todo lo que cubren y lo que NO cubren (huecos), con ejemplos locales reales.
2. Preguntas reales: "la gente también pregunta", sugerencias de autocompletado y búsquedas relacionadas -> cada una se responde en una lección o en la FAQ.
3. Fuentes primarias: documentación oficial (Google Search Central, Ayuda de Google Business Profile, Google Ads, Schema.org, etc.) y estudios con fecha. Todo dato o paso debe poder comprobarse; nada inventado. Si algo es opinión o experiencia, dilo.
4. Intención: define a quién ayuda y qué problema deja resuelto; el título lleva la búsqueda principal, la descripción promete el resultado.
5. Guarda las fuentes en `fuentes` (mínimo 4, https) y el estudio (SERP, huecos, preguntas) en investigacion/cursos/AAAA-MM-DD_slug.md.
6. Revisión final: sin promesas de posiciones, datos y pasos verificados, español claro para quien empieza.

## Formato del JSON
```
{
  "slug": "como-aparecer-en-google-maps-sin-pagar",
  "title": "...", "description": "... (140-160 car.)",
  "date": "AAAA-MM-DD (el lunes)",
  "area": "SEO | SEM | GEO | Google Business | Web",
  "character": "lumen|nuri|rumbo|tuerca",   // rumbo=Google Business, nuri=Academia/IA, tuerca=Web/SEO técnico, lumen=diagnóstico/SEO
  "nivel": "Inicial", "duracion": "1 h en total",
  "busqueda": "la búsqueda real a la que responde",
  "resultado": "qué tendrá la persona al terminar",
  "intro": "...",
  "para_quien": ["..."], "materiales": ["herramientas gratis"],
  "lecciones": [  // mínimo 3, ideal 5-7
    { "titulo": "...", "resumen": "...", "minutos": 3,
      "video": { "url": "https://cdn.jsdelivr.net/gh/Haruuth/levantehub-contenido@main/media/AAAA-MM-DD_slug/leccion-1.mp4", "titulo": "..." },
      "pasos": ["paso 1 concreto", "paso 2"],
      "aplicacion": "cómo aplicarlo hoy en TU negocio (ejemplo real)",
      "tarea": "algo que se hace y se puede comprobar" }
  ],
  "seguimiento": ["a los 7 días revisa...", "a los 30 días mide..."],
  "faq": [{"q":"...","a":"..."}],
  "fuentes": [{"nombre":"Documentación oficial ...","url":"https://..."}],
  "tags": ["..."]
}
```
`video` es opcional (solo .mp4 https). Las tareas se convierten en casillas de seguimiento que la persona marca (se guardan en su navegador).

## Reglas
- Todo gratis: sin precios, sin "comprar", sin registro. CTA: "Empezar", y mención suave a los servicios al final.
- Muy explicativo, fácil de aplicar, sin humo; datos y ejemplos reales de negocios locales (Valencia cuando proceda).
- Vídeos de lección: voz del personaje (ElevenLabs, `voces.json`), formato vertical como los tutoriales; si no se pueden generar ese lunes, publicar el curso sin vídeo y anotarlo.
- Tras publicar: crear el Reel/Short/post/story del lunes sobre el curso y enlazarlo, igual que la pieza de las 6:00.
