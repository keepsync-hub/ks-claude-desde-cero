# Claude desde Cero — landing del ebook

Landing de venta del ebook **Claude desde Cero**, publicada en GitHub Pages.

- **URL:** https://keepsync-hub.github.io/ks-claude-desde-cero/
  (⚠️ falta activar **Settings → Pages → Source: GitHub Actions** en este repo: hoy esa URL
  responde 404 y el sitio se sigue sirviendo desde el repo anterior.)
- **Lo que se vende acá es el ebook**, y nada más: enseña a usar Claude en el día a día hasta
  recuperar **16 horas a la semana** —dos días—, con el método completo: los hábitos, los
  Proyectos que guardan el contexto, las Skills que guardan el procedimiento y el trabajo sobre
  los archivos reales.
- **Oferta:** las primeras **20 reservas** pagan **USD 25**; después el ebook queda en **USD 50**.
- **La reserva y el pago van seguidos.** Al enviar el formulario se guarda el registro y la
  misma página manda a pagar a Webpay, sin salir del sitio. El correo con el mismo link queda
  de respaldo para quien prefiera pagar después, con 48 h de plazo.
- **El taller en vivo no se vende en la página: se cotiza.** Tiene su propia sección (`#taller`)
  con lo que incluye y un botón de WhatsApp, **sin cifra**: el formato y el precio dependen del
  tamaño del área. Esa venta es conversada y **no toca n8n**.

## La promesa, y de dónde sale

El número no es una frase de marketing suelta: la sección «De dónde salen las 16 horas» lo
desglosa en una tabla de seis tareas, y **la tabla tiene que cuadrar**.

| Tarea | Hoy | Con el método | Recupera |
|---|---|---|---|
| Correo, mensajes y respuestas | 6 h | 2 h | 4 h |
| Informes, minutas y resúmenes | 5 h | 1,5 h | 3,5 h |
| Planillas, cruces y reportes | 4 h | 1 h | 3 h |
| Documentos y propuestas | 4 h | 1,5 h | 2,5 h |
| Presentaciones | 3 h | 1 h | 2 h |
| Buscar y ordenar información | 2 h | 1 h | 1 h |
| **Total** | **24 h** | **8 h** | **16 h** |

**Si se edita una fila hay que rehacer el total**, y si el total deja de dar 16 hay que cambiar
también el titular, el hero, la portada del ebook, el `<title>`, la descripción y las dos
tarjetas OG. El «2 días» es esa misma cifra dicha de otra manera.

## Cómo se describe el producto

El ebook se cuenta **por el resultado**, no por las funciones: lo que se recupera, no la lista
de botones. Las tres piezas del método —Proyectos, Skills y el trabajo sobre archivos reales—
aparecen siempre con un ejemplo concreto de oficina. El cierre que lo diferencia: casi todo el
mundo usa Claude como un buscador con buenos modales; acá se usa como alguien a quien se le
delega, porque ya sabe cómo trabajas.

**Los cursos gratis se nombran, pero no se enlazan.** Existen y sostienen el método —son
dieciocho guías en cuatro niveles—, y por eso la página los usa como prueba de que el recorrido
está probado. Enlazarlos desde acá sería mandar a la gente a leer gratis a mitad de la venta.

## Cómo se le habla a quien lee

**Se tutea.** La página, los mensajes del formulario y el correo de confirmación tratan de **tú**
a quien reserva: «reserva tu copia», «te llega por correo», «escríbenos». Conviene revisarlo al
editar, porque el registro se rompe con una sola frase suelta en usted.

## Los precios que aparecen

| Precio | Qué es | Cómo se cobra |
|---|---|---|
| USD 25 / USD 50 | El ebook (lanzamiento / normal) | Formulario → n8n → link de pago, en la página y por correo |
| Sin cifra | El taller en vivo para el equipo | WhatsApp, fuera de la página |

El taller **no lleva precio escrito a propósito**: depende del tamaño del área y del formato. Si
alguna vez se le pone cifra, hay que agregarla también acá y revisar que el argumento de la
sección siga en pie.

## Cómo está armado

HTML, CSS y JavaScript estáticos, sin build ni dependencias. La página no carga **nada**
desde dominios externos: ni fuentes, ni frameworks, ni analítica. El único request que sale
es al webhook de n8n.

```
docs/
  index.html          la página completa (la portada del ebook es un SVG inline)
  assets/styles.css   estilos
  assets/reserva.js   contador de cupos + envío del formulario
  assets/og.png       imagen para compartir en redes (1200×630, capturada del propio hero)
  assets/fonts/       Space Grotesk y JetBrains Mono, servidas desde acá
  .nojekyll           por si alguna vez se vuelve a servir desde una rama
.github/workflows/
  pages.yml           empaqueta docs/ y lo publica en Pages
n8n/
  reserva-ebook.workflow.js   código SDK del workflow, fuente de verdad
```

## El lenguaje visual

El sistema de diseño **no se inventó acá**: es el mismo de «Claude desde Cero» en
[cristianignacio.me](https://cristianignacio.me/cursos/) —repo
[`keepsync-hub/cristianignacio.me`](https://github.com/keepsync-hub/cristianignacio.me)—,
copiado tal cual desde su `assets/css/style.css` para que las dos páginas se vean como una sola
cosa. Minimalista en estructura, neo-brutalista en color y forma: crema `#faf4e6`, tinta
`#16130d`, acentos planos (amarillo, rosa, cian, violeta, naranjo, lima), borde de 3 px, radio de
14 px, sombra dura sin blur y una trama de puntos de fondo.

`styles.css` está partido en dos por eso mismo:

| Parte | Qué es | Al editar |
|---|---|---|
| **1. Sistema heredado** | El CSS de la referencia, sin tocar | Si el sistema cambia allá, se vuelve a copiar entero |
| **2. Capa propia** | Formulario, oferta, contador, portada, FAQ, burbuja | Acá va todo lo que esta landing tiene y la referencia no |

Dos ajustes deliberados sobre lo heredado: la pila tipográfica no nombra fuentes de sistema de
ningún fabricante, y `.hp` —la trampa para bots— se oculta **fuera de pantalla** en vez de con
`display:none`, que es como estaba armado el formulario de esta landing.

### Las tipografías

**Space Grotesk** (400-700, variable) y **JetBrains Mono** (600), en `.woff2` latin descargadas a
`docs/assets/fonts/`: 44 KB entre las dos. Se sirven desde el propio sitio en vez de pedírselas a
Google Fonts, para que la página siga sin depender de un dominio externo.

Solo se bajó el subconjunto **latin**, que cubre el español completo (acentos, `ñ`, `¿`, `¡`, `«»`
y las comillas y rayas tipográficas). **Si alguna vez se escribe algo fuera de ese rango**
—griego, cirílico, vietnamita— hay que bajar también ese subconjunto o el texto caerá al
fallback.

### Las ilustraciones

No hay fotos: las tres piezas gráficas —la semana del hero, la portada del ebook y el mark `C0`—
son **SVG inline**, dibujadas con el mismo trazo de 3 px y los mismos acentos. No hay archivo que
cargar, no hay logo de terceros y se pueden editar como texto.

La semana del hero es la traducción visual de la tabla de las 16 horas: cinco días, tres con un
bloque rosado (lo repetitivo) y dos enteros en verde (lo que vuelve). **Si cambia la cuenta,
cambia el dibujo.**

## Publicar

La publicación va por **GitHub Actions**: el workflow `.github/workflows/pages.yml` empaqueta
`docs/` y lo despliega en Pages. Cada push a `main` que toque `docs/` republica solo; también
se puede lanzar a mano desde la pestaña Actions.

Para activarlo la primera vez hay que dejar **Settings → Pages → Source: GitHub Actions**
(una sola vez; si quedara en "Deploy from a branch", el workflow falla al desplegar).
**En este repo todavía no está activado.**

Para trabajar localmente:

```bash
python3 -m http.server 8099 -d docs
```

## El backend de las reservas

Un solo workflow de n8n, **Ebook Claude desde Cero · Reservas (GitHub Pages)**, con dos rutas:

| Ruta | Método | Devuelve |
|---|---|---|
| `/webhook/claude-desde-cero/cupos` | GET | `{ total, tomados, restantes, precio, precio_normal }` |
| `/webhook/claude-desde-cero/reserva` | POST | `{ ok, estado, cupo, restantes, link_pago }` |

Las reservas se guardan en la Data Table `reservas_claude_desde_cero`, que es la fuente de verdad.

### Los tres estados de una reserva

| Estado | Cuándo | Qué recibe la persona |
|---|---|---|
| `reservado` | Quedan cupos | Cupo numerado, salto al pago en la página y el link por correo |
| `ya_reservado` | El correo ya estaba | Su cupo original y el mismo salto al pago |
| `lista_espera` | Los 20 están tomados | Aviso de que le escribimos al salir a USD 50. **Sin salto al pago**: todavía no hay nada que cobrar, y por eso `link_pago` viene en `null` |

El guardado usa **upsert por correo**, así que el mismo correo dos veces actualiza su fila y
nunca duplica. El nodo `Responder al navegador` va después de guardar y antes de Gmail: la
persona recibe su confirmación rápido y un fallo de correo no le cuesta la reserva —y tampoco
le cuesta el pago, porque el link viaja en la respuesta del webhook, no solo en el correo.

### El salto al pago

Cuando la reserva queda confirmada, `reserva.js` inserta un botón **Pagar ahora** bajo el
formulario y salta solo al link a los 4 segundos. Ese retraso es a propósito: da tiempo a leer
que el cupo quedó tomado y no empuja a nadie sin aviso; si el salto automático falla o el
navegador lo bloquea, el botón sigue ahí.

El link sale de `data.link_pago`, que devuelve el webhook. `reserva.js` guarda además una copia
en la constante `LINK_PAGO` como respaldo, y solo acepta la del servidor si viene por `https://`.
**Si cambia el link de pago hay que cambiarlo en los dos lugares**: `LINK_PAGO` en
`n8n/reserva-ebook.workflow.js` (que alimenta el correo y la respuesta) y `LINK_PAGO` en
`docs/assets/reserva.js` (el respaldo).

### El contrato entre la página y `reserva.js`

`reserva.js` no se toca al editar el contenido, pero **depende del HTML**. Si se reescribe una
sección, esto tiene que seguir existiendo o el formulario deja de funcionar en silencio:

| Selector | Para qué |
|---|---|
| `form.reserva` (×2: hero y cierre) | los formularios que intercepta |
| `form[data-origen]` | se envía como campo `origen` |
| `nombre`, `email`, `website`, `consentimiento` | los campos del POST |
| `[data-cupos]` (×2) | el texto del contador |
| `.form-status` dentro del form | los mensajes de estado (`is-on` + `is-ok` / `is-wait` / `is-err`) |
| `.btn-primary` dentro del form | se le cambia el texto y se deshabilita |
| `.microcopy` dentro del form | se reemplaza cuando se agotan los cupos |

El bloque de pago (`.pago`, `.pago-btn`, `.pago-aviso`) lo crea el script: en el CSS solo hay que
tenerlo estilado.

### Anti-spam

El formulario lleva un campo trampa `website`, oculto por CSS y fuera del foco. El webhook
descarta la petición antes de ejecutar un solo nodo si ese campo viene con algo o si el
correo no tiene forma de correo (`onlyRunIf`), y además ignora bots y sólo acepta peticiones
desde `https://keepsync-hub.github.io`.

### Contacto directo

La página lleva una burbuja fija de WhatsApp al número de contacto
(`+56 9 9412 0579`, enlace `wa.me` con mensaje prellenado). Es también el
respaldo cuando el formulario falla, cuando el visitante tiene JavaScript
desactivado, y la vía para pedir que se borren los datos.

Hay **dos mensajes prellenados distintos** sobre el mismo número, para saber en la bandeja
con qué intención llega cada persona:

| Mensaje | Dónde está |
|---|---|
| «tengo una consulta» | Burbuja fija, pie de página, cierre y el `noscript` de los formularios |
| «quiero cotizar el taller de Claude para mi equipo» | Botón de la sección `#taller` |

Los dos van percent-encoded en el HTML para no equivocarse con los acentos.

### Si n8n no responde

La página no se rompe. El contador se queda con el texto estático del HTML ("Solo 20 copias
a este precio") y el formulario sigue enviable. Un fallo al enviar deja el formulario
reenviable y ofrece el WhatsApp del autor como respaldo.

## Estado

**El backend está montado y activo.** El workflow
`Ebook Claude desde Cero · Reservas (GitHub Pages)` corre en n8n cloud:

| Pieza | Valor |
|---|---|
| Workflow | `l3iJs9bH4XpqQAWh` — [abrir en n8n](https://keepsync-hub.app.n8n.cloud/workflow/l3iJs9bH4XpqQAWh) |
| Data Table | `reservas_claude_desde_cero` → `KPRHxEzOjaL3txG3` |
| Credencial de correo | Gmail OAuth2 `cYhcyiH1LcyrXUWz`, remitente «Claude desde Cero» |
| Link de pago | `https://www.webpay.cl/form-pay/420828` |

El archivo `n8n/reserva-ebook.workflow.js` sigue siendo la fuente de verdad: es el
código con el que se creó el workflow, con el ID de la tabla ya pegado en `TABLA`.
**Si se edita el workflow desde la interfaz de n8n, hay que reflejar el cambio acá**,
o la próxima importación pisa lo editado.

La Data Table **se renombró, no se recreó**: conserva el ID `KPRHxEzOjaL3txG3` y todas las filas
que ya tenía.

### Cómo se verificó el cambio de nombre

| Prueba | Resultado |
|---|---|
| Contrato DOM en el navegador | Los dos `form.reserva`, los cuatro campos, los dos `[data-cupos]`, `.form-status`, `.btn-primary` y `.microcopy`: todos presentes |
| Envío del formulario con n8n interceptado | POST con `{nombre, email, consentimiento, website, origen:"hero"}`, contador actualizado, botón **Pagar ahora USD 25** insertado |
| Layout a 1440 px y a 390 px | Sin scroll horizontal en ninguno de los dos |
| Dominios externos | Ninguno: solo el webhook, `wa.me` y Webpay |
| Workflow de n8n con datos pinchados | `success`; correo generado con el nombre, el tuteo y la paleta nuevos, y `respuesta.link_pago` correcto |

**Si pruebas el webhook con `curl` y te responde `403 Authorization data is wrong!`, no está
roto**: el webhook lleva `ignoreBots: true` y el `User-Agent` de curl cae como bot. Con un
`User-Agent` de navegador responde 200 normal:

```bash
curl -A "Mozilla/5.0 (X11; Linux x86_64; rv:126.0) Gecko/20100101 Firefox/126.0" \
  -H "Origin: https://keepsync-hub.github.io" \
  https://keepsync-hub.app.n8n.cloud/webhook/claude-desde-cero/cupos
```

### Lo único que no es automático

El pago **se valida a mano**: el formulario de Webpay no avisa de vuelta a n8n, así que
`pagado` se marca a mano y **un cupo reservado y no pagado queda tomado** hasta que alguien
lo libere. Con 20 cupos eso se administra mirando la tabla; si el volumen crece, ahí sí
conviene el workflow de conciliación que está más abajo.

Para borrar filas de prueba hay un workflow desechable archivado en n8n, que borra lo que tenga
`origen = prueba-tecnica` —un valor que ninguna reserva real puede traer, porque la landing manda
`hero` o `cierre`—. Está archivado a propósito: para usarlo hay que desarchivarlo primero.

## Pendiente (fase 2)

- **Activar Pages en este repo** (Settings → Pages → Source: GitHub Actions). Hasta que eso pase,
  la URL canónica del `<head>` apunta a una página que todavía no existe.
- **Renombrar el workflow de limpieza archivado en n8n**, que sigue llevando el nombre del
  producto anterior.
- **Embudo propio para el taller.** Hoy esa venta sale por WhatsApp y no queda registrada en
  ninguna parte. Medirla exigiría un segundo workflow y otra Data Table; se dejó fuera a
  propósito, porque es una venta conversada y el formulario no la mejora.
- **Declarar formato, duración y precio del taller** en la página. Hoy dice "lo coordinamos por
  WhatsApp", que es honesto pero convierte peor que un dato escrito.
- Espejo de la Data Table a un Google Sheet, con un workflow programado aparte. Queda fuera
  del camino de la reserva a propósito: un fallo de credencial ahí no le cuesta una venta a
  nadie. Requiere crear una credencial de Google Sheets en n8n.
- **Conciliación de pagos:** marcar `pagado` y liberar los cupos vencidos a las 48 h. Hoy es
  manual y no se puede automatizar del todo: el formulario de pago no notifica a n8n. Lo que sí
  se puede hacer es un workflow programado que libere los cupos con más de 48 h y `pagado = false`,
  dejando la confirmación del pago como el único paso a mano.
