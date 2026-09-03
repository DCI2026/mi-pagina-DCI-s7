# CLAUDE.md

Este archivo lo lee Claude cada vez que trabaja en esta carpeta, sin que se lo pidas.
Lo vas a llenar en la sesión. Por ahora trae solo las reglas que aplican desde el
primer minuto.

---

## 1. Qué es este proyecto y quién lo usa

*(Lo escribes tú en la sesión: dos líneas. Qué es la página, para quién es y cada
cuándo se usa.)*

## 2. De dónde sale cada cifra

Los datos de esta página viven en una tabla de Supabase llamada `registros`.
Ninguna cifra ni ningún texto que se muestre se escribe a mano en el HTML: todo
sale de esa tabla o de lo que la persona escriba en el formulario.

La tabla `registros` tiene estas columnas:

| Columna | Qué guarda | Quién la llena |
|---|---|---|
| `nombre` | Texto. El nombre de quien escribe. | La persona, en el formulario. Obligatorio. |
| `mensaje` | Texto. Lo que quiere decir. | La persona, en el formulario. Obligatorio. |
| `creado_en` | La fecha y hora en que se guardó. | Se pone sola. Sirve para ordenar del más nuevo al más viejo. |
| `id` | Un número que distingue cada renglón. | Se pone solo. La página no lo muestra. |

**Quién puede hacer qué con la tabla:** cualquiera puede **leer** y **agregar**.
Nadie puede **borrar** ni **modificar**. No hace falta una regla que lo prohíba:
en Supabase lo que no se autoriza queda prohibido solo. Por eso la página no
tiene botón de borrar, y no se lo agregues: sería un botón que siempre falla.

**Cómo se conecta la página.** En `index.html` están escritos, a la vista, los
dos datos que hacen falta: la liga `https://vxsstmgblaxfrxwqlzjk.supabase.co` y
la llave que empieza con `sb_publishable_`. Que estén a la vista es correcto —
ver la sección 4.

## 3. Cómo quiero que trabajes aquí

- Antes de un cambio grande, dame el plan por escrito y espera mi visto bueno.
- Un cambio a la vez. Enséñame qué cambió antes de escribirlo.
- Trabaja siempre en una rama, nunca directo sobre `main`.
- No publiques a producción sin que yo lo pida: fusionar es una decisión mía.
- **Si tienes acceso a mi base de datos, enséñame el SQL antes de correrlo y espera mi
  respuesta.** Crear o borrar tablas, agregar o quitar columnas y cambiar permisos no se
  deshacen con una rama: en cuanto corren, ya está.

## 4. Lo que nunca debes hacer

- **Nunca escribas en esta carpeta una llave que empiece con `sb_secret_` o que
  diga `service_role`.** La única llave que puede estar aquí es la que empieza
  con `sb_publishable_`, que está hecha para andar a la vista.
- No inventes datos. Si algo no está en la tabla, que la página diga que no hay
  nada todavía, no un ejemplo.
- No borres el historial ni fuerces cambios sobre lo ya publicado.

## 5. Mi regla de verificación

*(La escribes tú en la sesión: con qué frase cierras lo que entregas y qué tiene
que ser cierto para que puedas publicarlo.)*

## 6. Cómo vuelvo a abrir esto

- El proyecto vive en este repositorio de GitHub.
- Se abre pidiéndole a Claude una sesión sobre este repo; no hace falta descargarlo.
- La página publicada está en la liga que da Netlify.
- La base de datos está en supabase.com, en el proyecto de esta cuenta.

> **Si la página deja de mostrar datos después de una semana sin usarla**, casi
> siempre es que el proyecto gratuito de Supabase se pausó. Se despierta con el
> botón **Resume project**.
