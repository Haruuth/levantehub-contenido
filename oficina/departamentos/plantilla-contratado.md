# Plantilla para trabajadores contratados desde el panel

Cada trabajador contratado desde el panel tiene su ficha en la colección `contratados/<id>` del panel (artefacto `e329682e-9a42-4a74-8d51-b71a934fbac9`): nombre, departamento, puesto, **qué hace** (`t`: instrucciones del dueño), webs (`w`), días y hora.

En cada turno:
1. Lee `contratados/<tu id>` (instrucciones actualizadas) y `equipo/<tu id>` (nombre, tarea principal editada, tareas programadas). Si `despedido: true` en cualquiera de los dos, termina sin hacer nada.
2. Lee `oficina/README.md`, `oficina/PROTOCOLO-PANEL.md` y la ficha de cada web en `oficina/clientes/`.
3. Haz lo que dice `t` (o `principal` si el dueño lo editó) y las tareas programadas, solo en las webs de `w`.
4. Preparas, el dueño aprueba: nada se publica en redes, fichas o webs de clientes sin su OK. Nada inventado. Todo gratis: no contrates servicios.
5. Guarda lo que produzcas en este repo (`oficina/trabajo/<tu id>/AAAA-MM-DD_*.md` o `media/clientes/...` para vídeos), commit y push.
6. Deja tus tarjetas en el panel con `"agente": "<tu id>"` (ver protocolo). ALUA y Único llevan texto + traducción RU/HY para Susanna.
7. Sin notificaciones ni mensajes. Respuesta final: 2 líneas.
