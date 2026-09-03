# MI PROYECTO DCI

Página de práctica para aprender a construir con Claude sin escribir código. No es de un cliente y nadie depende de ella: si se rompe, no pasa nada. Está publicada en **https://mi-pagina-dci-s7.netlify.app** y cualquiera con la liga puede escribir en ella.

## Qué muestra, y de dónde sale

Dos pestañas: **Comentarios** (dejar uno, y responder a los de otros) y **Propuestas** (sugerir qué le falta a la página).
Ninguna cifra ni ningún texto está escrito a mano en el HTML: todo sale de Supabase, de las tablas `comentarios` y `propuestas`. Cualquiera puede leer y agregar; **nadie puede borrar ni modificar**, ni siquiera el dueño desde la página. Las columnas de cada tabla están en `CLAUDE.md`, sección 2.

## Qué hay en `.claude`

`agents/revisor-antes-de-publicar.md` — un revisor que mira la página antes de que salga a internet y reporta tres cosas: llaves secretas metidas en el repositorio, faltas de ortografía, y enlaces que se lleven al visitante a otros sitios. **No arregla nada**: solo tiene permiso de leer, así que no puede aunque quiera. Se le pide diciendo "revisa antes de publicar".

## Qué hacer para continuar

1. Lee `CLAUDE.md` antes que nada. Son las reglas de la casa y Claude las obedece sin que se las recuerdes.
2. Abre una sesión de Claude sobre este repositorio. No hace falta descargarlo ni instalar nada.
3. Pide el cambio en español. Claude trabaja en una rama, abre un Pull Request y lo lleva hasta producción él solo — salvo tocar la base de datos, que sí te pide permiso primero, porque eso no se deshace.

> Si la página deja de mostrar datos tras una semana sin usarla, casi siempre es que el proyecto gratuito de Supabase se pausó. Se despierta con el botón **Resume project**.
