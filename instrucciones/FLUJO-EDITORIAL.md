# FLUJO EDITORIAL DE LEVANTEHUB (cadena de relevo)

Regla de oro: cada departamento trabaja POR ADELANTADO para el siguiente. Nadie empieza de cero: recibe el trabajo ya preparado del anterior. Este flujo es el estándar actual y está abierto a cambios; si el dueño cambia algo, se edita aquí.

## Cadena diaria
1. ROMU (Director SEO, análisis) — trabaja el día anterior y por la noche. Investiga demanda real (Search Console, Google Trends, competencia) y deja el informe `investigacion/demanda/AAAA-MM-DD.md` y el tema de MAÑANA en `investigacion/cola-diaria.json` (tipo, slug, por qué, huecos, fuentes, enlaces previstos). Se sabe qué se publicará ANTES de que se escriba.
2. CLARA (redacción) — por la mañana (tarea de las 6:03) lee el informe de Romu y escribe y publica la pieza del día: tutorial, guía, novedad o recomendación. Enlaza todo (ver ROMU-demanda-y-temas.md).
3. LEO (vídeo) — con la pieza publicada, genera el reel (Instagram) y el Short (YouTube) de ese día. Todo tutorial lleva vídeo con gancho; el resto, reel/Short cuando toque.
4. MONICA Y MILA (traducciones) — traducen al inglés y al ruso la pieza y también los textos y títulos de los vídeos, acto seguido.
5. SUSI (supervisión) — comprueba que todo está publicado y enlazado y actualiza el Panel. Un solo aviso al día.

## Cadena semanal
- Lunes: DR. JOAN escribe el curso gratis de la semana (preparado a partir del informe semanal de Romu) y MONICA Y MILA lo traducen a EN y RU.
- Domingo: informe SEMANAL de cada departamento (ver abajo) y el de Romu manda el tema del curso del lunes.

## Informes de cada departamento (todos, igual)
- DIARIO (antes de entregar su trabajo al siguiente): 3-5 líneas con lo que ha mirado, qué eligió y por qué. Romu: informe de demanda completo.
- SEMANAL (domingo): todo lo buscado, publicado y medido esa semana; qué funcionó y qué no; propuesta de la semana siguiente. Guardar en `investigacion/semanal/AAAA-Snn.md` (Romu) o `oficina/departamentos/<dept>/semanal/AAAA-Snn.md` (el resto).
- MENSUAL (día 1): resumen del mes anterior con tendencia (crecimiento, %), mejores y peores piezas y objetivos del mes. Mismas rutas con `AAAA-MM.md`.
- Los números siempre con su fuente y fecha; lo relativo se etiqueta como relativo; sin dato = «sin dato».

## Seguimiento de tráfico (analista de tráfico)
Cada semana mide las 5 webs y sus fichas de Google y guarda números y capturas en el repositorio PRIVADO (`levantehub-web/seguimiento/<web>/AAAA-Snn/`). Ver ANALISTA-TRAFICO-seguimiento-semanal.md. Romu usa esos números para decidir temas.

## Cierre del día de Leo
Tras publicar reel, Short, posts e historias, Leo actualiza las historias destacadas para que la pieza del día quede en su destacada (instrucciones/LEO-publicacion-e-historias-destacadas.md).
