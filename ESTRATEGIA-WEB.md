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
