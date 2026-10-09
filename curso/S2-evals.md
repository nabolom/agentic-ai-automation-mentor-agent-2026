## Sesión 2 — Evals: mide tu decisión de IA, desde cero

En la Sesión 1 diseñaste tu sistema y quedaron una o dos decisiones en manos de la IA. La Sesión 2 responde una sola pregunta: **¿cuánto acierta esa decisión?** No "se ve bien". Un número.

Esta sección tiene dos partes. **Parte A** son los conceptos — léela con calma, idealmente antes del taller. **Parte B** es el taller paso a paso — ahí vas a copiar y pegar. No las mezcles: primero entiende, luego ejecuta.

---

## Parte A — Los conceptos (léelos antes de tocar nada)

### ¿Qué es un eval?

Un eval es **un caso de prueba con dos cosas. Nada más:**

| Parte | Qué es | Ejemplo |
|---|---|---|
| **Input** | Lo que entra a tu sistema | Correo: «su producto llegó roto» |
| **Salida esperada** | Lo que DEBERÍA salir, escrito por ti antes de correr nada | `categoría: queja` |

No es una herramienta cara ni un framework. Con diez de estos tienes con qué medir.

**La regla que lo vuelve real:** la salida esperada tiene que poder verificarse **sin preguntarle al modelo si acertó**. Un campo concreto: una categoría, un sí/no, un valor.

| ✅ Salida esperada bien escrita | ❌ Mal escrita (no verificable) |
|---|---|
| `categoría: queja` | "que clasifique bien el correo" |
| `resultado: escalar` | "que se dé cuenta de que falta la OC" |
| `monto: 14200` | "una respuesta razonable" |

Si para saber si acertó tendrías que opinar, el caso está mal escrito.

### ¿Qué es "el prompt" que vamos a medir?

Es la instrucción que tu sistema le da a Claude para tomar SU decisión — la que quedó como IA en tu `flujo.md` de la Sesión 1. Vive en un archivo de tu proyecto: `proyectos/<tu-proyecto>/prompts.md`. Si aún no lo tienes, el agente te ayuda a crearlo en el **Paso 2**, justo antes de correr `/eval` — lo traduce desde tu diseño de la Sesión 1 (`decisiones.md` y `reglas.md`).

Cada vez que lo cambies, la versión anterior se queda escrita (v0, v1, v2…). Nunca borres una versión: comparar los números entre versiones es justamente el punto.

### Dónde se hace cada cosa (no te pierdas)

Vas a alternar entre dos lugares que se ven parecidos pero no son lo mismo:

| Lugar | Cómo se ve | Qué haces ahí |
|---|---|---|
| **Terminal** | El prompt de tu sistema (`%` o `$`) | Comandos como `ls`, `curl`, `git`, y arrancar `claude` |
| **Claude Code** | Conversación con el agente (entraste con `claude`) | Hablar con el agente y correr `/eval`, `/arrancar`, etc. |

Para salir de Claude Code y volver a la terminal: `Ctrl+C` (o escribe `/exit`). Para volver a entrar: `claude`.

### ¿Por qué los casos van ANTES que el prompt?

Pregunta justa — parecería natural escribir primero el prompt y luego probarlo. El orden es al revés a propósito:

> **La verdad se fija antes de medir.** Si escribes el prompt primero, vas a escribir — sin darte cuenta — casos que tu prompt ya resuelve, y el número saldrá bonito y mentiroso. Si fijas los 10 casos primero (con sus salidas esperadas), el prompt se enfrenta a una realidad que no puede acomodar. Es la misma razón por la que un examen se escribe antes de ver las respuestas del alumno.

Además, tu prompt v0 no nace de la nada: se traduce desde tu `decisiones.md` y `reglas.md` de la Sesión 1. El diseño ya existe; el prompt solo lo pone en palabras. Por eso escribirlo toma 2 minutos en el Paso 2, mientras que los casos — que sí requieren TU conocimiento de la operación — se llevan el Paso 1 completo.

---

## Parte B — El taller, paso a paso

La ruta completa, para que sepas siempre dónde estás:

| Paso | Qué haces | Dónde | Qué queda en disco |
|---|---|---|---|
| **0** | Actualiza tu repo (trae `/eval` y la plantilla) | 📍 Terminal | `.claude/commands/eval.md`, `proyectos/PLANTILLA-evals.md` |
| **1** | Escribe tus 10 casos (la verdad, primero) | 📍 Claude Code | `evals.md` con inputs y salidas esperadas |
| **2** | Escribe tu prompt v0 y corre la línea base | 📍 Claude Code | `prompts.md` (v0) + tu primer número |
| **3** | Diagnostica los fallos, agrega SOLO el contexto pedido | 📍 Claude Code | `prompts.md` (v1, sin borrar v0) |
| **4** | Vuelve a correr y compara v0 vs v1 | 📍 Claude Code | `evals.md` con una columna por versión |

Cada paso cierra con un commit. Al final del taller, tu `git log` cuenta la historia completa: la verdad → el número feo → el porqué → el número mejor.

---

### Paso 0 — Trae el comando `/eval` y la plantilla a TU repo 📍 EN LA TERMINAL

Si creaste tu repo desde esta plantilla **antes** de la Sesión 2, tu copia no tiene `/eval` ni la plantilla de evals (los repos creados desde template NO reciben actualizaciones automáticas — son una foto del día que los creaste).

Abre la terminal y entra a tu repo (si no sabes dónde quedó, es la carpeta donde clonaste; corre `pwd` para ver dónde estás):

```bash
cd ~/proyectos-ia/TU-REPO   # ajusta la ruta a donde clonaste el tuyo
```

Verifica si ya tienes el comando:

```bash
ls .claude/commands/
```

Si en la lista aparece `eval.md`, ya está: salta al Paso 1. Si NO aparece, copia y pega estas dos líneas (descargan el comando y la plantilla directo de este repo):

```bash
curl -o .claude/commands/eval.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/.claude/commands/eval.md
curl -o proyectos/PLANTILLA-evals.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/proyectos/PLANTILLA-evals.md
```

Confirma que llegaron y guárdalos en tu repo:

```bash
ls .claude/commands/          # debe aparecer eval.md
ls proyectos/                 # debe aparecer PLANTILLA-evals.md

git add .claude/commands/eval.md proyectos/PLANTILLA-evals.md
git commit -m "sesion 2: comando /eval y plantilla de evals"
git push
```

**Importante:** si tenías Claude Code abierto, ciérralo (`Ctrl+C`) y vuelve a entrar (`claude`). Los comandos nuevos solo se detectan al arrancar.

---

### Paso 1 — Escribe tus 10 casos ANTES de correr nada 📍 EN CLAUDE CODE

> Primero la verdad, luego el prompt. Si te saltaste el porqué, está en la Parte A.

El camino fácil: copia la plantilla a tu proyecto y llénala con ayuda del agente. Dentro de Claude Code, pégale esto (ajusta el nombre de tu proyecto):

```
Copia proyectos/PLANTILLA-evals.md a proyectos/<tu-proyecto>/evals.md y ayúdame
a llenarla. La decisión que quiero evaluar es la más difícil de mi decisiones.md.
Hazme preguntas sobre mi operación para construir los casos — no los inventes tú.
```

El reparto de los 10 casos no es negociable:

| Cuántos | Tipo | Qué son |
|---|---|---|
| 5 | Típicos | El caso normal de todos los días |
| 3 | Límite | Raros pero reales, sacados de TU operación (el redondeo, el caso fronterizo) |
| 2 | Adversariales | Diseñados para romperla: input vacío, datos que faltan, un intento de manipulación |

> Si los 10 casos fueran del camino feliz, el número mentiría hacia arriba. Los casos límite y adversariales son los que te dicen la verdad.

Tú pones los casos reales y decides la salida esperada de cada uno. El agente arma la tabla. **No dejes que el agente invente los casos: un número construido con casos inventados es ficción.**

**¿Se te dificulta escribir los casos?** Es normal — es la parte más difícil de la sesión. Lee [`proyectos/GUIA-escribir-evals.md`](../proyectos/GUIA-escribir-evals.md): tiene recetas por tipo de decisión (clasificar, extraer, decidir, redactar) con tablas completas para calcar, el truco de "no escribas casos, recuerda casos", y un prompt para llenar la tabla con el agente de uno en uno. Si vas contra reloj: 6 casos reales (4 típicos, 1 límite, 1 adversarial) bastan para una primera medición honesta.

---

### Paso 2 — Escribe tu prompt v0 y corre la línea base 📍 EN CLAUDE CODE

Primero necesitas el prompt que vas a medir. Si aún no tienes `prompts.md`, pídeselo al agente — que lo arme desde tu diseño de la Sesión 1, **mínimo, sin adornos**:

```
Escribe la versión v0 del prompt para la decisión que estoy evaluando, usando mi
decisiones.md y mi reglas.md. Que sea mínima: solo la instrucción y las reglas,
sin contexto de negocio ni ejemplos. Guárdala en proyectos/<tu-proyecto>/prompts.md como v0.
```

Pelón a propósito: quieres medir el punto de partida más crudo, para que la mejora del contexto se note después. Con el v0 en su lugar, mídelo:

```
/eval
```

El agente toma tus 10 casos, los corre contra tu prompt v0, compara cada salida contra la verdad que TÚ escribiste, y te da la tasa: `6/10`, `7/10`, lo que salga. **Ese número feo es tu línea base — tu punto de partida medido.** No lo maquilles.

Guárdalo con un commit 📍 EN LA TERMINAL (o pídele al agente que lo haga):

```bash
git add proyectos/
git commit -m "eval: corrida v0 - 6/10"
git push
```

---

### Paso 3 — Diagnostica y agrega SOLO el contexto que los fallos pidieron 📍 EN CLAUDE CODE

Por cada caso que falló (❌), el agente te dice en qué nivel de la escalera cae, en este orden:

| Nivel | Pregunta | Ejemplo de arreglo |
|---|---|---|
| 1 | ¿La regla está escrita ambigua? | Reescribir "si coincide" → "si la diferencia es menor a $0.50" |
| 2 | ¿Le falta un dato? | Una lista de alias de proveedores, un catálogo, una tolerancia |
| 3 | ¿Era un `if` disfrazado? | Sacarlo del prompt: eso se resuelve con código, no con IA |
| 4 | ¿Es el modelo? | **Casi nunca es el modelo.** Es el último escalón, no el primero |

La disciplina: agrega únicamente el contexto que un eval reprobado pidió. Nada especulativo, ni un documento más. El agente actualiza tu `prompts.md` con la versión nueva (v1) **sin borrar la v0**.

---

### Paso 4 — Vuelve a correr y compara 📍 EN CLAUDE CODE

```
/eval
```

Cada versión del prompt deja su propia columna en tu `evals.md`. Ver el número subir de v0 a v1 — con el porqué escrito al lado — es tu evidencia de que el sistema mejoró. Commit y push otra vez.

**Regla permanente desde hoy: cada vez que toques un prompt, corre `/eval`.** Arreglas un caso y sin querer rompes otros tres; sin la suite, te enteras en producción. Los prompts se rompen igual que el código, pero fallan más callados.

---
