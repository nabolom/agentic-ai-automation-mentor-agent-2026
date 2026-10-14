# Empieza aquí — Aprendedor(a)

Esta página es tu **orientación ampliada**. No necesitas leer todo el repositorio antes de empezar.

> **Si tu siguiente actividad es S2, ve primero a la [Ruta crítica antes de S2](docs/ruta-critica-antes-de-s2.md).** Esa es la única ruta canónica: 60–90 minutos, una decisión, seis casos y un fallback.

## Tu objetivo

Vas a convertir una automatización o una idea en un sistema que puedas explicar, medir y dejar operable por otra persona.

```text
proceso → decisión → evals → diagnóstico → límites → handoff
```

No es obligatorio construir un agente autónomo. Justificar un workflow con un solo paso de IA, o decidir no automatizar todavía, también es un resultado válido.

## 1. Elige tu ruta

| Si… | Empieza por… |
|---|---|
| Tu siguiente actividad es S2 | [`Ruta crítica antes de S2`](docs/ruta-critica-antes-de-s2.md) |
| Ya tienes proceso, automatización, seis casos y una falla documentada | La **fast lane** dentro de la ruta crítica |
| Tienes una idea, pero todavía no un proceso acotado | La ruta crítica y después `/arrancar` |
| No tienes entorno o la herramienta no funciona | [`Camino dorado`](ejemplo/README.md), offline o en papel |
| Trabajas en n8n, Make, Cowork u otra herramienta visual | Ruta crítica; el contrato y la evidencia son los mismos |

## 2. Primera entrada: 15 minutos

1. Usa la plantilla de GitHub para crear tu copia privada, o trabaja en la copia que ya tienes.
2. Elige **Claude Code o Cowork**. No necesitas ambas herramientas.
3. Consulta [`Dependencias y preflight`](docs/dependencias-y-preflight.md) solo para verificar la ruta que elegiste o resolver un bloqueo.
4. Ve a la [Ruta crítica antes de S2](docs/ruta-critica-antes-de-s2.md) y sigue su checklist.

Si no tienes Python, Git o autenticación lista, no detengas el aprendizaje: abre [`ejemplo/casos.json`](ejemplo/casos.json), recorre los seis casos y conserva la evidencia para office hours.

## 3. Qué debes traer a S2

La preparación mínima es:

- un proceso propio o el caso común;
- una sola decisión de IA;
- seis casos: 4 típicos, 1 límite y 1 adversarial;
- la salida esperada de cada caso;
- una ruta de fallback si la herramienta falla.

No necesitas crear todavía todos los archivos del proyecto. `flujo.md`, `alcance.md`, `decisiones.md`, `reglas.md` y `evals.md` se construyen o completan durante S2.

## 4. Cómo pedir acompañamiento

Dentro de Claude Code o Cowork puedes decir:

```text
Lee CLAUDE.md, ACOMPANAMIENTO.md y docs/ruta-critica-antes-de-s2.md.
Hazme una pregunta a la vez.
Ayúdame a preparar una sola decisión de una automatización.
No avances hasta que pueda explicar if, IA, validación y humano.
No inventes mis salidas esperadas: ayúdame a fijarlas.
Si no tengo un proceso acotado, usa el camino dorado como andamio.
```

El acompañamiento cambia según tu evidencia:

- **Nivel 0–1:** explicación breve, ejemplo y una pregunta.
- **Nivel 2:** reto y evidencia faltante: número, archivo o criterio.
- **Nivel 3:** revisión como par: riesgos y contradicciones.

## 5. Qué no necesitas hacer todavía

- No necesitas construir un agente autónomo.
- No necesitas conectar una API real.
- No necesitas instalar Node/NPM si tu proyecto no los usa.
- No necesitas usar n8n si tu proceso vive en otra herramienta.
- No necesitas construir un loop.
- No necesitas completar diez casos.
- No necesitas traer datos sensibles reales.

## 6. Cómo sabrás que avanzaste

Puedes responder:

1. ¿Qué parte es un `if`?
2. ¿Qué parte necesita IA y por qué?
3. ¿Cuánto acierta sobre tus seis casos?
4. ¿Cómo sabes que funcionó sin preguntarle al modelo?
5. ¿Qué acción nunca dejarías automática?
6. Si tú desapareces mañana, ¿quién lo corre?

## Referencias bajo demanda

- [Ruta de la cohorte](curso/00-ruta-de-la-cohorte.md)
- [Camino dorado](ejemplo/README.md)
- [Mapa de competencias](docs/competencias.md)
- [Guía de instalación](docs/instalacion.md)

El resto del repositorio es referencia bajo demanda; no es una lista de lectura obligatoria.
