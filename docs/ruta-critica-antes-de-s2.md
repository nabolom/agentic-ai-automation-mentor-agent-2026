---
type: ruta-critica
title: Ruta de preparación y continuidad de S1+S2
description: Preparación técnica y continuidad después de la primera sesión de trabajo: una decisión, seis casos y un fallback claro.
tags: [ruta, s1-s2, onboarding, evals]
timestamp: 2026-10-13T00:00:00Z
---

# Ruta de preparación y continuidad de S1+S2

> **Ruta principal de la primera sesión:** empieza por [`S1+S2 — Panorama de Agent Engineering Q4-2026`](../curso/S1-S2-panorama-y-evals.md). Esta página conserva el preflight, la fast lane y los pasos para cerrar los seis casos después del laboratorio.

**Duración independiente:** 60–90 minutos. **En clase:** forma parte del laboratorio de 75 minutos.

**Resultado de continuidad:** cerrar una decisión acotada, seis casos núcleo y una ruta de fallback. En la sesión, el mínimo observable es una decisión y tres casos ancla.

**Orden:** repositorio y Claude Code; camino dorado primero; proyecto propio después.

> **Regla:** antes de construir un agente, fija el proceso, la decisión, la salida esperada y cómo sabrás si funcionó.

## Dependencias antes de empezar

No instales todo el ecosistema. Elige una ruta y consulta la [`Guía de dependencias y preflight`](dependencias-y-preflight.md) solo si necesitas instalar algo o resolver un bloqueo:

- **Código/API:** Git + Claude Code + Python son la combinación recomendada.
- **Cowork/visual:** Cowork + acceso al repo bastan para comenzar.
- **JavaScript/TypeScript, n8n local o MCP:** Node.js + NPM solo si tu proyecto los necesita.

La ruta nativa de Claude Code **no necesita Node ni NPM**. Las API keys tampoco son requisito antes de S2.

## Si ya tienes una automatización: fast lane de 30–45 minutos

No repitas todo el onboarding. Usa el camino dorado solo como calibración del contrato y pasa a tu proceso propio si ya puedes mostrar:

- un proceso acotado;
- una sola decisión de IA;
- seis casos con salidas esperadas;
- una falla, traza o resultado que puedas discutir.

Hazlo así:

1. Recorre el diagrama del camino dorado y confirma que distingues `if`, IA, validación y humano.
2. Corre `/rumbo` solo para fijar foco, alcance y qué llevarás a S2.
3. Transfiere el criterio a tu proceso propio.
4. Revisa tus seis casos 4/1/1 y marca el caso que más te preocupa.
5. Elige una extensión, no varias: costo, harness, loop, MCP o multiagente.

La fast lane produce la misma llegada: proceso, decisión, seis casos, salidas esperadas y fallback.

## Ruta común, paso a paso

Si todavía no tienes una automatización, no empieces por `/rumbo`. Primero mira y entiende el caso común.

### Paso 0 — Abre tu copia

Crea tu copia privada con **Use this template** o abre la copia que ya tienes. Entra a la carpeta con Claude Code o Cowork. No instales nada adicional todavía.

**Checkpoint:** puedes abrir el repositorio y sabes dónde está la carpeta `ejemplo/`.

### Paso 1 — Mira el ejemplo común

Abre [`ejemplo/README.md`](../ejemplo/README.md) y lee solamente **Problema** y **La secuencia que enseña**. El camino dorado es un caso común de solicitudes que van a soporte, ventas, facturación o revisión humana; no es un producto que tengas que construir.

**Checkpoint:** puedes explicar en una frase qué decide el sistema.

### Paso 2 — Identifica las cuatro etapas

Antes de ejecutar, escribe una respuesta breve:

1. ¿Qué se resuelve con un `if`?
2. ¿Cuándo entra la IA?
3. ¿Dónde se valida la salida?
4. ¿Cuándo decide una persona?

**Checkpoint:** tienes una nota con las cuatro respuestas.

### Paso 3 — Ejecuta el ejemplo offline

En macOS/Linux:

```bash
python3 ejemplo/camino_dorado.py --modo offline --version v1
```

En Windows:

```powershell
py ejemplo/camino_dorado.py --modo offline --version v1
```

Si no tienes Python, abre [`ejemplo/casos.json`](../ejemplo/casos.json), recorre los seis casos núcleo con el diagrama y anótalos en una tabla. No necesitas API key ni conexión a una API.

**Checkpoint:** tienes una corrida de `v1` o una tabla manual de los seis casos.

### Paso 4 — Comprueba que entendiste

Responde:

- ¿Qué casos no llegan a la IA?
- ¿Qué hace la IA cuando sí entra?
- ¿Qué pasa si la salida no valida?
- ¿Por qué un caso termina en humano?
- ¿Qué mejora `v1` respecto a `v0`?

**Checkpoint:** puedes explicar el recorrido sin leer el diagrama.

### Paso 5 — Define tu foco con acompañamiento

Ahora sí, ejecuta `/rumbo` o pide a Claude Code/Cowork:

```text
Lee CLAUDE.md, ACOMPANAMIENTO.md y docs/ruta-critica-antes-de-s2.md.
Hazme una pregunta a la vez.
Ayúdame a elegir un solo proceso o caso.
No avances hasta que pueda explicar if, IA, validación y humano.
No inventes mis salidas esperadas.
```

**Checkpoint:** tienes `rumbo.md` o una nota equivalente con foco, alcance y qué llevarás a S2.

### Paso 6 — Prepara tu llegada a S2

Fija una decisión de IA, seis casos —4 típicos, 1 límite y 1 adversarial—, la salida esperada de cada caso y un fallback.

**Checkpoint final:** puedes enseñar proceso/caso, decisión, seis casos, salidas esperadas y fallback.

## Mensaje corto para cerrar la primera medición

Si solo vas a compartir una instrucción, comparte esta:

```text
Después de la sesión S1+S2, no construyan un agente completo. Cierren la primera medición siguiendo estos pasos (60–90 min):

1. Abran su copia y luego `ejemplo/README.md`.
2. Lean “Problema” y “La secuencia que enseña”.
3. Identifiquen `if`, IA, validación y humano.
4. Corran el ejemplo offline; si no tienen Python, usen `casos.json` en papel.
5. Respondan las cinco preguntas de comprensión.
6. Ejecuten `/rumbo` con acompañamiento, una pregunta a la vez.
7. Fijen una decisión, seis casos, salidas esperadas y fallback.

Para S2 deben poder mostrar: proceso/caso, una decisión, seis casos, salidas esperadas y una ruta de fallback.

No necesitan conectar una API real, usar n8n, construir un loop, completar diez casos ni hacer multiagente.
```

## Resultado esperado

En 60–90 minutos —o en 30–45 minutos si aplica la fast lane— el Aprendedor(a) debe llegar a S2 con:

1. entorno comprobado o un fallback claro;
2. el camino dorado recorrido o entendido;
3. `/rumbo` ejecutado o iniciado;
4. un proceso propio o el caso común elegido;
5. una sola decisión de IA;
6. un borrador de seis casos núcleo y sus salidas esperadas.

## Orden obligatorio

1. **Abrir la copia** — elegir Claude Code o Cowork; no instalar todo el ecosistema.
2. **Leer el ejemplo** — abrir `ejemplo/README.md` y entender el problema.
3. **Observar el contrato** — identificar `if`, IA, validación y humano.
4. **Ejecutar o simular** — correr `v1` offline o usar `casos.json` en papel.
5. **Comprobar comprensión** — responder las cinco preguntas antes de transferir.
6. **Rumbo y transferencia** — elegir un proceso propio o quedarse con el caso común.
7. **Contrato y evals** — fijar una decisión, seis casos y sus salidas esperadas.
8. **Paquete de llegada** — guardar `rumbo.md` y llevar evidencia, no promesas.

## Timebox recomendado

| Minutos | Acción | Salida |
|---:|---|---|
| 0–5 | Abrir la copia y elegir Claude Code o Cowork. | Repositorio accesible. |
| 5–15 | Leer `ejemplo/README.md`: Problema y secuencia. | Una frase que explique el sistema. |
| 15–25 | Identificar `if`, IA, validación y humano. | Nota con cuatro respuestas. |
| 25–35 | Correr `v1` offline o recorrer `casos.json` en papel. | Corrida o tabla de seis casos. |
| 35–45 | Responder las cinco preguntas de comprensión. | Explicación propia del contrato. |
| 45–65 | Ejecutar `/rumbo` con una pregunta a la vez. | `rumbo.md`, foco y alcance. |
| 65–90 | Fijar una decisión, seis casos y sus salidas esperadas. | Tabla 4/1/1 y fallback. |

## Qué debe poder mostrar el Aprendedor(a)

En menos de tres minutos:

- “Este es el proceso o caso que estoy trabajando”.
- “Esta es la única decisión que quiero medir”.
- “Estos son mis seis casos: 4 típicos, 1 límite y 1 adversarial”.
- “Esta es la salida esperada y esta es la acción que nunca dejo automática”.
- “Si mi entorno falla, esta es mi ruta offline”.

## Qué guardar

- `rumbo.md` con su frontmatter y la sección **Qué llevo a S2**.
- Una frase de alcance: qué queda dentro y qué queda fuera.
- Un contrato inicial de entrada y salida.
- Seis casos núcleo y sus salidas esperadas.
- Una captura, transcript o nota del camino dorado/fallback.

No necesitas que todos los archivos del proyecto estén completos antes de S2. Necesitas llegar con criterio visible y una decisión que pueda medirse.

## Fallbacks

| Si ocurre esto… | Haz esto… |
|---|---|
| Claude Code o auth no funcionan | Trabaja en Cowork, con el camino dorado o en papel. |
| Git no está listo | Usa Cowork, ZIP o papel para no bloquear el aprendizaje; instala Git después para commits. |
| No tienes Python | Abre `ejemplo/casos.json` y recorre los seis casos manualmente. |
| No tienes Node/NPM | Continúa: solo son necesarios para JS/TS, n8n local o MCP que los requiera. |
| No tienes proceso propio | Usa el camino dorado; la transferencia queda para S2. |
| No tienes tiempo para seis casos | Termina `/rumbo`, fija una decisión y lleva los casos incompletos marcados; S2 los completa. |
| Te tienta construir un agente completo | Detente: primero contrato, casos y criterio de éxito. |

## Qué NO hacer para cerrar la primera medición

- No conectes una API real por demostrar que puedes.
- No uses datos sensibles reales.
- No construyas un loop si todavía no tienes una línea base.
- No completes diez casos por cumplir un número.
- No uses multiagente para resolver un problema que aún no puedes describir en una frase.
- No conviertas la instalación en el objetivo de la sesión.

## Referencias rápidas

- [Empieza aquí como Aprendedor(a)](../ALUMNO-EMPIEZA-AQUI.md)
- [Dependencias y preflight](dependencias-y-preflight.md)
- [Competencias de Agentic AI](competencias.md)
- [Camino dorado](../ejemplo/README.md)
- [Ruta de la cohorte](../curso/00-ruta-de-la-cohorte.md)
- [Guía anterior de `/rumbo`](antes-de-s2.md)
