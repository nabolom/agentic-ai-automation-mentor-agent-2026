# Sesión de trabajo S1+S2 — Panorama de Agent Engineering Q4-2026 y primera medición

> **Esta es la primera sesión técnica de la cohorte.** La reunión anterior fue de bienvenida, contexto y orientación. Aquí empieza el trabajo con el repositorio y el Agente Mentor.

## Qué vamos a lograr

En esta sesión vas a pasar de una idea, un proceso o una automatización existente a **una decisión concreta que podamos observar y medir**.

No necesitas construir un agente completo. Al terminar, debes poder distinguir:

```text
if → IA → salida estructurada → validación → humano
```

Y debes tener una primera decisión, tres casos ancla y un siguiente paso claro.

## Panorama de Agent Engineering Q4-2026

Las herramientas y los modelos cambian rápido. El criterio que nos interesa practicar es más estable:

> **El modelo genera; el sistema organiza, recuerda, verifica y limita.**

Agent Engineering no significa poner un LLM en cada paso. Significa diseñar un sistema capaz de ejecutar trabajo verificable, con reglas donde convienen reglas, IA donde existe ambigüedad real y una persona donde el riesgo o la incertidumbre lo exige.

El repositorio, Claude Code y el Agente Mentor son el entorno de trabajo. No son el objetivo de la sesión.

## Agenda de 150 minutos

| Minutos | Bloque | Qué ocurre | Evidencia de salida |
|---:|---|---|---|
| 0–30 | Plenaria de cohorte | Panorama, vocabulario, promesa y dos rutas de trabajo | Cada persona sabe qué trae y qué track le corresponde |
| 30–65 | Teoría aplicada | Decisión, contrato, eval, salida esperada y diagnóstico | Todas las personas entienden el caso común |
| 65–75 | Break | Pausa real; no se usa para instalar | Pregunta o bloqueo anotado |
| 75–150 | Laboratorio con Claude Code | Abrir repo, cargar Mentor, definir foco y producir evidencia | Repo abierto, decisión, tres casos ancla y siguiente paso |

Si la conversación teórica necesita 45 minutos, termina a los 75 y deja 65 minutos de laboratorio. **No reduzcas la plenaria ni elimines el fallback.**

## Bloque 1 — Plenaria de cohorte · 30 minutos

La plenaria responde cuatro preguntas:

1. ¿Qué cambia cuando un paso de automatización puede decidir?
2. ¿Qué diferencia hay entre un workflow, un chatbot y un agente?
3. ¿Qué significa que el resultado sea verificable?
4. ¿Qué vamos a construir, medir y defender durante el curso?

El mapa de la cohorte es:

```text
proceso → decisión → evals → diagnóstico → límites → handoff
```

No se presenta como una clase de “estado del arte”. El nombre visible es **Panorama de Agent Engineering Q4-2026**, porque toda afirmación temporal debe entenderse con su fecha de corte.

## Bloque 2 — Teoría aplicada · 30–45 minutos

La teoría solo cubre lo que se usará inmediatamente:

1. **Una decisión no es todo un agente.** Primero acota qué debe decidir el sistema.
2. **No todo pasa por IA.** Un `if` debe seguir siendo un `if`; lo irreversible o incierto puede escalar a una persona.
3. **Un eval tiene input y salida esperada.** La salida esperada la fija quien conoce la operación, antes de correr el sistema.
4. **El núcleo es de seis casos.** Cuatro típicos, uno límite y uno adversarial. Los diez son una extensión opcional.
5. **La tasa es una señal, no una verdad total.** `aciertos / casos` permite ver un punto de partida y decidir qué diagnosticar.
6. **Se cambia una cosa a la vez.** Se corren los mismos casos y se explica qué cambió.

La demostración común usa el camino dorado:

```text
entrada → reglas/if → IA solo para ambigüedad → salida estructurada → validación → humano o ruta final
```

## Bloque 3 — Laboratorio con Claude Code · 75 minutos

### Paso 1 — Abre tu entorno

Si ya tienes una copia del repositorio, abre la terminal en esa carpeta:

```bash
claude
```

Si todavía no tienes copia, usa la plantilla de GitHub y créala como privada. La [guía de instalación](../docs/instalacion.md) tiene las rutas actuales para macOS, Linux/WSL y Windows.

Dentro de Claude Code, verifica el contexto del proyecto:

```text
Lee CLAUDE.md y ACOMPANAMIENTO.md.
Dime qué repositorio abrí, qué hace el Agente Mentor y qué comandos del proyecto están disponibles.
No edites archivos todavía.
```

Claude Code carga los archivos del proyecto según los necesita; los comandos y skills del proyecto viven en `.claude/`. Si aparece una solicitud de permiso, lee qué acción se propone antes de aprobarla.

### Paso 2 — Elige tu track

No todas las personas deben hacer lo mismo.

| Track | Si llegas con… | Tu objetivo en esta sesión |
|---|---|---|
| **Descubrir** | Una idea o proceso, pero ninguna automatización | Elegir un proceso acotado y una decisión que valga la pena explorar |
| **Construir** | Un prototipo o automatización que solo tú puedes correr | Separar `if`, IA, herramienta y humano; definir una primera decisión |
| **Endurecer** | Una automatización que ya funciona, pero falla o no tiene medición | Elegir una decisión difícil, una falla y una línea base posible |
| **Productificar / escalar** | Algo que ya corre para otras personas | Identificar el cuello de botella, el costo, el riesgo o el handoff que falta |

Pide al Mentor que te ayude con el track, sin que invente evidencia:

```text
Lee CLAUDE.md y ACOMPANAMIENTO.md.
Hazme una pregunta a la vez.
Ayúdame a elegir entre descubrir, construir, endurecer o productificar/escalar.
No inventes mi proceso, mis casos ni mis salidas esperadas.
Si todavía no tengo un proceso acotado, usa el camino dorado como andamio.
```

Después puedes ejecutar `/rumbo` para fijar tu ruta formal. `/rumbo` mide; el acompañamiento ayuda a interpretar la evidencia después.

### Paso 3 — Usa el camino común

Abre [`ejemplo/README.md`](../ejemplo/README.md). Lee **Problema**, **Qué vas a hacer aquí** y **La secuencia que enseña**.

Si todavía no tienes proceso propio, trabaja con este caso. No es una versión inferior del curso: es el andamio común para aprender el contrato.

Si ya tienes automatización, usa el camino dorado durante cinco minutos y luego transfiere el criterio a **una sola** decisión de tu sistema.

### Paso 4 — Produce tu primera evidencia

El mínimo de la sesión es:

- una frase de proceso o caso;
- una sola decisión de IA;
- tres casos ancla: uno típico, uno límite y uno adversarial;
- la salida esperada de cada caso;
- una duda concreta o siguiente paso.

No necesitas terminar los seis casos en el laboratorio. **Los tres casos ancla hacen visible que entendiste el método.** La suite de seis —4 típicos, 1 límite y 1 adversarial— queda como la entrega inmediata para cerrar S2.

Para quien vaya más rápido, el laboratorio puede continuar con los seis casos, `/eval`, la línea base y el diagnóstico de un fallo.

## Cierre de la sesión

Debes poder decir:

> “Este es el proceso o caso. Esta es la decisión que quiero medir. Este es un caso normal, este es el caso límite y este intenta romper la decisión. Estas son sus salidas esperadas. Esto es lo que todavía no sé.”

## Entrega inmediata después de la sesión

Completa la suite núcleo de seis casos y guarda:

- seis inputs recordados de tu operación o del camino dorado;
- cuatro típicos, uno límite y uno adversarial;
- la salida esperada fijada por ti;
- una línea base cuando tu herramienta esté lista;
- el caso que más te preocupe y por qué.

No conectes una API real para cumplir un número. No uses datos sensibles. Si Claude Code, Git, Python o la autenticación fallan, conserva la evidencia y usa el camino dorado offline o en papel.

## Mensaje breve para el grupo

> Hoy empieza nuestro trabajo técnico. Primero veremos el **Panorama de Agent Engineering Q4-2026** y después entraremos al repositorio con Claude Code. No necesitas llegar con un agente terminado. Según lo que traigas, vas a descubrir un proceso, construir una primera automatización, endurecer una que ya existe o preparar su escalamiento. La meta de hoy es una decisión de IA, tres casos ancla, sus salidas esperadas y un siguiente paso. Los seis casos completos cierran la primera medición después de la sesión.
