# CLAUDE.md

Este archivo lo lee Claude cada vez que trabaja en esta carpeta, sin que se lo pidas.

---

## 1. Qué es este proyecto y quién lo usa

Es una **página de prueba**: existe para que yo aprenda a usar Claude. No es de
un cliente, no es para trabajo real y nadie depende de ella.

Tiene dos pestañas: **Comentarios**, donde cualquiera deja un comentario del
proyecto y puede responder a los de otros, y **Propuestas**, para sugerir qué le
falta a la página. Está publicada y abierta: cualquier persona con la liga puede
escribir, y nadie puede borrar lo escrito.

La uso mientras dure el curso. Como es de práctica, si algo se rompe no pasa
nada: se puede tirar y volver a empezar. Aquí puedes proponerme cosas y
equivocarte sin drama — lo único que sí me importa es que me digas la verdad de
qué probaste y qué no.

## 2. De dónde sale cada cifra

Los datos de esta página viven en Supabase. Ninguna cifra ni ningún texto que se
muestre se escribe a mano en el HTML: todo sale de esas tablas o de lo que la
persona escriba en el formulario.

### Tabla `comentarios`

| Columna | Qué guarda | Quién la llena |
|---|---|---|
| `nombre` | Texto. Quién escribe. | La persona. Obligatorio. |
| `comentario` | Texto. Lo que dice. | La persona. Obligatorio. |
| `responde_a` | El `id` del comentario al que le responde. Vacío si no le responde a nadie. | La página, cuando alguien usa el botón Responder. |
| `creado_en` | La fecha y hora en que se guardó. | Se pone sola. Ordena la lista. |
| `id` | Un número que distingue cada renglón. | Se pone solo. |

**Una respuesta es un comentario que apunta a otro.** Por eso no hay una segunda
tabla de respuestas, y por eso las respuestas se ven colgando de su comentario.

### Tabla `propuestas`

| Columna | Qué guarda | Quién la llena |
|---|---|---|
| `nombre` | Texto. Quién propone. | La persona. Obligatorio. |
| `propuesta` | Texto. Qué propone. | La persona. Obligatorio. |
| `creado_en` | La fecha y hora en que se guardó. | Se pone sola. |
| `id` | Un número que distingue cada renglón. | Se pone solo. |

### Tabla `registros`

Quedó de un ejercicio anterior, con las columnas `nombre` y `mensaje`. **La
página ya no la usa** y está vacía. No la borres sin preguntarme.

### Quién puede hacer qué, en las tres tablas

Cualquiera puede **leer** y **agregar**. Nadie puede **borrar** ni **modificar**.
No hace falta una regla que lo prohíba: en Supabase lo que no se autoriza queda
prohibido solo. Por eso la página no tiene botón de borrar, y no se lo agregues:
sería un botón que siempre falla.

### Cómo se conecta la página

En `index.html` están escritos, a la vista, los dos datos que hacen falta: la
liga `https://vxsstmgblaxfrxwqlzjk.supabase.co` y la llave que empieza con
`sb_publishable_`. Que estén a la vista es correcto — ver la sección 4.

## 3. Cómo quiero que trabajes aquí

- Antes de un cambio grande, dame el plan por escrito y espera mi visto bueno.
- Un cambio a la vez. Enséñame qué cambió antes de escribirlo.
- Trabaja siempre en una rama, nunca directo sobre `main`.

### Termina lo que empiezas: ningún cambio se queda en una rama

**Cualquier cambio, en cualquier rama, se lleva hasta el final sin que yo te lo
pida.** No me dejes ramas sueltas ni Pull Requests abiertos esperando mi permiso
para publicar. Los cuatro pasos son uno solo:

1. **Abre el Pull Request.**
2. **Fusiónalo a `main`.**
3. **Deja todo desplegado en producción**: la página en Netlify y la base de
   datos en Supabase. Si un cambio toca las dos cosas, las dos quedan aplicadas,
   no una sí y otra no.
4. **Compruébalo con datos y dime la liga**, como pide la sección 5.

### La única cosa que sí me tienes que preguntar

**Si tienes acceso a mi base de datos, enséñame el SQL antes de correrlo y espera
mi respuesta.** Crear o borrar tablas, agregar o quitar columnas y cambiar
permisos no se deshacen con una rama: en cuanto corren, ya está.

**Esta regla NO la cancela la de arriba.** Publicar sin preguntar, sí. Destruir
sin preguntar, no. Son cosas distintas: una se puede revertir, la otra no.

## 4. Lo que nunca debes hacer

- **Nunca escribas en esta carpeta una llave que empiece con `sb_secret_` o que
  diga `service_role`.** La única llave que puede estar aquí es la que empieza
  con `sb_publishable_`, que está hecha para andar a la vista.
- No inventes datos. Si algo no está en la tabla, que la página diga que no hay
  nada todavía, no un ejemplo.
- No borres el historial ni fuerces cambios sobre lo ya publicado.

## 5. Mi regla de verificación

Cuando me entregues algo, cierra con esta frase:

> **Probado, no supuesto.**

Y solo la escribes si de verdad es cierta. Antes de la frase, dime en tres
renglones:

1. **Qué probaste de verdad** y qué te contestó la prueba. No "debería
   funcionar": qué corriste y qué salió.
2. **Qué NO pudiste probar**, y por qué.
3. **Qué me toca revisar a mí** con mis propios ojos.

Si no probaste algo, no escribas la frase. **Prefiero un "no pude" que un "ya
quedó".** Si me dices que algo sirve y no sirve, no me sirves de nada; si me
dices que no sabes, todavía te puedo creer lo demás.

### Publicar ya no me pide permiso, pero sí me rinde cuentas

La sección 3 te deja publicar sin preguntarme. El trato es que a cambio, **cada
vez que publiques** me dejes por escrito:

- **La liga** de lo que quedó publicado.
- **La prueba de que el despliegue de verdad quedó**: su estado, y que el commit
  publicado es el mismo que fusionaste. El dato, no un "ya está".
- **Qué no pudiste probar** y qué me toca revisar a mí.

### Estas dos son obligatorias antes de publicar, aunque yo no esté

- **No hay ninguna llave `sb_secret_` ni `service_role` en la carpeta** (sección 4).
- **Nada de lo que muestra la página está inventado**: o sale de una tabla, o sale
  de lo que escribió la persona (sección 2).

Si alguna de las dos no se cumple, **no se publica**. Ahí sí párate y pregúntame,
aunque eso deje el cambio a medias.

## 6. Cómo vuelvo a abrir esto

- El proyecto vive en este repositorio de GitHub.
- Se abre pidiéndole a Claude una sesión sobre este repo; no hace falta descargarlo.
- La página publicada está en **https://mi-pagina-dci-s7.netlify.app**.
- La base de datos está en supabase.com, en el proyecto `curso-claude-ejemplo`.

> **Si la página deja de mostrar datos después de una semana sin usarla**, casi
> siempre es que el proyecto gratuito de Supabase se pausó. Se despierta con el
> botón **Resume project**.
