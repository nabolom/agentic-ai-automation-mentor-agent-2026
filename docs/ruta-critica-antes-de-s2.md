---
type: ruta-critica
title: Ruta crítica antes de S2
description: Preparación de 60–90 minutos para llegar a S2 con una decisión, seis casos y un fallback claro.
tags: [ruta, pre-s2, onboarding, evals]
timestamp: 2026-10-13T00:00:00Z
---

# Ruta crítica antes de S2

> **Fuente canónica:** si tu siguiente actividad es S2, esta es la única ruta que necesitas seguir. Las demás guías son apoyo o referencia técnica.

**Duración:** 60–90 minutos

**Resultado:** llegar a S2 con una decisión acotada, seis casos núcleo y una ruta de fallback.

**Orden:** camino dorado primero; proyecto propio después.

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

## Mensaje corto para hoy

Si solo vas a compartir una instrucción, comparte esta:

```text
Antes de S2, no construyan un agente completo. Hagan esta ruta en orden (60–90 min):

1. Consulten la guía de dependencias y elijan Claude Code o Cowork.
2. Instalen/verifiquen solo lo que necesita su ruta; Node/NPM son opcionales.
3. Abran su copia del repo en Claude Code o Cowork.
4. Corran el camino dorado offline v1; si no tienen Python, recorran `ejemplo/casos.json` en papel.
5. Ejecuten `/rumbo` y guarden `rumbo.md`.
6. Elijan UN proceso propio o quédense con el caso común.
7. Escriban UNA decisión de IA; no diseñen todo el agente.
8. Traigan seis casos: 4 típicos, 1 límite y 1 adversarial, con su salida esperada.

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

1. **Dependencias y preflight** — elegir ruta; verificar solo Git, Claude Code/Cowork y Python cuando correspondan.
2. **Camino dorado** — primero el caso común, sin credenciales.
3. **Rumbo** — qué quieres construir, qué puedes demostrar y qué ruta te conviene.
4. **Transferencia** — elegir un proceso propio o quedarse conscientemente con el caso común.
5. **Contrato** — fijar una sola decisión y su salida esperada.
6. **Evals** — 4 típicos, 1 límite y 1 adversarial.
7. **Paquete de llegada** — guardar `rumbo.md` y llevar evidencia, no promesas.

## Timebox recomendado

| Minutos | Acción | Salida |
|---:|---|---|
| 0–10 | Consultar la matriz de dependencias, ejecutar el preflight de la ruta elegida y documentar cualquier falla. | Entorno listo o fallback seleccionado. |
| 10–25 | Correr el camino dorado offline v1, o recorrer `casos.json` en papel. | Vocabulario común: `if` → IA → validación → humano. |
| 25–60 | Ejecutar `/rumbo` y completar sus decisiones de entrada. | `rumbo.md` y sección “Qué llevo a S2”. |
| 60–75 | Elegir un proceso propio o el caso común y escribir una sola decisión de IA. | Una frase de alcance y contrato inicial. |
| 75–90 | Escribir seis casos núcleo y su salida esperada. | Tabla 4/1/1; si no termina, lleva el borrador y marca el hueco. |

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

## Qué NO hacer antes de S2

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
