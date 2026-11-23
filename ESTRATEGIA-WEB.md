# Estrategia de LevanteHUB (decidida por Haruuth el 22-nov-2026)

## Objetivo
La web trabaja de forma pasiva: la mejor web en español para APRENDER SEO, SEM y GEO (posicionamiento en IAs), sin vender humo y sin vender cursos. Se gana tráfico orgánico con contenido útil, abierto y gratuito. No se vende nada en la web salvo los dos servicios que se mantienen: SEO local y ficha de Google Business. Más adelante se podrá añadir afiliación de Amazon (AAWP); no antes de tener tráfico orgánico.

## Reglas de contenido (todas las piezas y todas las redes)
- Todo curso, guía, tutorial, novedad y recomendación es GRATIS y público. Ningún precio de curso en la web ni en las publicaciones.
- Cada pieza responde a una consulta real (Search Console vía Windsor.ai, Google Trends, capturas en investigacion/search-console/) y cubre mejor que la competencia lo que ya posiciona.
- Temario abierto organizado en tres áreas: SEO, SEM y GEO. Cada pieza nueva se enlaza internamente con el resto de su área (related) y apunta a la siguiente lección.
- Llamada a la acción principal: leer, guardar y compartir contenido gratuito. Los servicios (SEO local, ficha de Google) solo como mención suave al final, sin precios agresivos.
- Nada inventado: fuentes oficiales para afirmaciones técnicas.

## Cambios pendientes en el código de la web (repo Haruuth/levantehub-web; requieren una sesión con acceso a ese repo)
1. Los 3 cursos ya generados pasan a abiertos: sin acceso privado, sin login/paywall, páginas públicas indexables (robots index, follow), incluidas en sitemap y enlazadas desde /guias y la portada.
2. Quitar los precios de cursos en toda la web (portada, páginas de curso, FAQ, schema.org Offer, metadatos, sitemap/llms.txt si los hubiera, textos de CTA tipo «comprar», «matricularse», «precio»). Mantener los precios y CTAs de los servicios SEO local y ficha de Google solo donde ya existan.
3. Cambiar los CTAs de cursos a «Empezar gratis».
4. Asistente de IA (botón abajo a la derecha, no el diagnóstico): mejorar precisión y coherencia. Pasos: revisar su prompt de sistema y su base de conocimiento; darle como fuente los JSON de levantehub-contenido/guias (recuperación por similitud o por palabras clave); obligarle a responder solo con lo que sabe de la web o de fuentes oficiales y a decir «no lo sé» y ofrecer contacto cuando no lo sepa; respuestas cortas con enlace a la guía exacta; no prometer resultados ni precios; tono cercano en español de España; registrar preguntas sin respuesta para crear contenido nuevo; batería de 30 preguntas de prueba antes de desplegar.
5. Preparar huecos de afiliación (AAWP) pero desactivados.

## Vídeo: reglas
- Todos los reels y Shorts llevan VOZ y SUBTÍTULOS siempre. Cada personaje tiene su propia voz e identidad (guardar voice_id en tools/instagram/voces.json). Si no se puede generar voz, no se programa: se deja en media/ y se avisa.
- Los personajes están en primer plano: presentan, señalan y enseñan en pantalla la guía, tutorial, novedad o recomendación del día.
- Mismo tema que la pieza de las 6:00. Reel optimizado para Instagram; Short con formato distinto, adaptado a YouTube.
- Formatos virales: cada semana se estudian los Shorts y Reels con más tracción en español sobre SEO, marketing digital y negocios locales (solo estructura y tipo de gancho, nunca copiar contenido ni material con copyright) y se anota en investigacion/formatos-virales.md.

## Tema de la pieza de las 6:00: lo que se habla en las redes (regla del dueño, 23-nov-2026)
- El tema de cada día debe salir de lo que se está hablando AHORA en redes y buscadores sobre Google Business, SEO local, IA para negocios y herramientas de Google/Meta/YouTube/Instagram: busca con WebSearch en noticias, foros, Reddit, X, YouTube e Instagram (qué preguntan, qué se comparte, qué novedades están generando conversación).
- Cruza esa tendencia con una consulta real (Search Console / Trends) y con la competencia; si coincide, ese es el tema. Si no hay tendencia clara, usa la cola de investigación.
- Anota en `por_que` de cola-diaria.json la señal social concreta (qué se dice, dónde, fecha y URL). Nada inventado.
- La investigación de la pieza de mañana (paso 7) debe aplicar esta misma regla.

## REGLAS DEL DUEÑO DEL 23-NOV-2026 (PREVALECEN sobre los prompts de las tareas 6:00, 7:03 y 8:07)
Haruuth ha rechazado el contenido de hoy por básico, largo y plano. A partir de ahora, en la web, en reels, Shorts, stories y posts:

1. **Valor real, no obviedades.** Cada pieza debe enseñar cosas que la mayoría de la gente NO sabe: trucos, atajos, ajustes ocultos, herramientas gratuitas poco conocidas, errores que casi todos cometen, datos oficiales recientes. Prohibido explicar lo evidente («entra, pulsa, copia») como contenido principal. Mínimo 3 tips «poco conocidos» verificados en fuente oficial en cada pieza, y deben aparecer en el título, el gancho y el reel. «Explicado a un niño de 5 años» queda ELIMINADO (sustituye ese bloque por la respuesta directa con el dato clave).
2. **Mostrar cómo usar la IA y herramientas gratuitas** en todas las guías y tutoriales cuando encaje: por ejemplo, generar un QR con la herramienta oficial o con Chrome (compartir > crear código QR), crear formularios gratis con Google Forms, o pedir a ChatGPT/Gemini/Claude textos y listas con un prompt exacto que el lector pueda copiar. Pon el prompt real entre comillas en la pieza y enséñalo en pantalla en el vídeo. Verifica cada herramienta y ruta de menú en su documentación oficial; nada inventado.
3. **Slugs cortos** (páginas nuevas): máximo 4-5 palabras y 40 caracteres, solo con la palabra clave (ej. `pedir-resenas-google`, `qr-resenas-google`). Prohibidos slugs-frase de 8+ palabras. Los slugs ya publicados no se cambian.
4. **Nada de biblia:** la pieza se lee en 4-6 minutos. Tutorial: 900-1.300 palabras, directas, con el tip estrella arriba. Guías: 700-1.000. Radar: 250-400. Calidad por encima de longitud; cada párrafo debe aportar algo que no esté en la competencia.
5. **Reels y Shorts virales** (ver tools/instagram/PLAYBOOK.md, «Lecciones del 23-nov»): gancho en el primer segundo con un dato sorprendente o un error que cuesta dinero, una frase de voz por escena, escenas de 2-4 s, texto grande que cambia sin parar, Lumen/personaje hablando (la boca se mueve), el truco poco conocido como protagonista y un cierre que invita a guardar. Short 45-60 s. Nunca una frase fija en pantalla más de 3 s.
6. **Orden de trabajo:** primero el tip estrella y el gancho, después la pieza web, después los vídeos; la pieza de las 6:00 se elige por lo que se habla ahora en redes (ver regla anterior).
