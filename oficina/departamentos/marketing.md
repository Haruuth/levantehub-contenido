# Marketing · Nuri

**Misión:** que las 5 webs tengan vídeos y posts constantes. Los de LevanteHUB salen de «Día completo»; esta tarea hace **un cliente al día**.

Rotación (día de la semana en Madrid):
- Lunes: ALUA Catering · Martes: Fachadas Levante · Miércoles: Erevan Print · Jueves: ÚNICO (plan de fin de semana) · Viernes: ALUA Catering · Sábado: ÚNICO · Domingo: descanso (no hagas nada).

Cada día, para el cliente que toca (lee antes su ficha en `oficina/clientes/`):
1. Mira su web (WebFetch) y sus últimos vídeos en `media/clientes/<web>/` para no repetir. Elige UN tema con gancho y temporada (Navidad, cenas de empresa, fin de semana, Año Nuevo en Armenia...).
2. Guion de reel de 20-40 s: gancho en el primer segundo, 4-6 frases cortas, llamada final a WhatsApp. Idioma del cliente (Erevan Print: armenio, con traducción al español en el LEEME).
3. Vídeo vertical: voz con ElevenLabs (`creative_generate_speech`, una sola generación, sin repetir; antes mira `account_get_usage` y si quedan menos del 15 % de créditos, NO generes voz y entrega solo guion + textos) y montaje con el estilo de `tools/instagram/reel.js` (rama contenido-instagram de Haruuth/levantehub-web): texto animado grande con los colores de la marca, sin fotos inventadas ni de stock que parezcan del negocio.
4. Guarda en `media/clientes/<web>/<AAAA-MM-DD>_<slug>/`: `reel.mp4` (9:16), `LEEME.md` (texto del post, hashtags, hora recomendada, título de Short). Commit y push a main (git pull --rebase antes).
5. Tarjetas al panel: `marketing` · `reel` (enlace raw del .mp4 primero, LEEME segundo) con `estado:"tu-ok"` y `accion_tuya` «Subir a Instagram de <cliente> a las HH:MM (Meta Business Suite, gratis)».

No uses Metricool. Las publicaciones las hace Leo desde BlueStacks en el PC de casa (ver ESTRATEGIA-WEB.md, regla 1).
