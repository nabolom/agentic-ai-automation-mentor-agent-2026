<h1 align="center">Agentic AI &amp; Automation Mentor Agent 2026</h1>

<p align="center"><strong>Curso avanzado para convertir automatizaciones en sistemas medibles, gobernables y operables por otra persona.</strong></p>

<p align="center">
  <img src="docs/visuales/repo-header.png" alt="Ilustración de Raúl Sisniega: zorro y gato frente a un sintetizador" width="100%">
</p>

<p align="center"><sub>Ilustración: <a href="https://www.behance.net/biosisniega">Raúl Sisniega</a> ©</sub></p>

<p align="center">
  <a href="LICENSE"><img alt="Licencia MIT" src="https://img.shields.io/badge/License-MIT-0F766E.svg"></a>
  <a href="https://github.com/nabolom/agentic-ai-automation-mentor-agent-2026/actions/workflows/validate.yml"><img alt="Validación" src="https://github.com/nabolom/agentic-ai-automation-mentor-agent-2026/actions/workflows/validate.yml/badge.svg?branch=main"></a>
  <a href="https://www.python.org/"><img alt="Python 3.11+" src="https://img.shields.io/badge/Python-3.11%2B-3776AB.svg?logo=python&amp;logoColor=white"></a>
  <a href="https://code.claude.com/docs/en/overview"><img alt="Workflow compatible con Claude Code" src="https://img.shields.io/badge/Workflow-Claude%20Code-5B5BD6.svg"></a>
  <a href="ALUMNO-EMPIEZA-AQUI.md"><img alt="Ruta compatible con Cowork" src="https://img.shields.io/badge/Ruta-Cowork-0EA5A4.svg"></a>
  <a href="docs/competencias.md"><img alt="Nivel avanzado" src="https://img.shields.io/badge/Nivel-Avanzado-E77B52.svg"></a>
  <a href="ejemplo/README.md"><img alt="Núcleo de seis casos" src="https://img.shields.io/badge/Núcleo-6%20casos-172033.svg"></a>
</p>

## 🚦 Antes de S2 — paso a paso

**Tiempo orientativo:** 60–90 minutos. **Hoy no vas a construir un agente completo.**

> **¿Ya tienes una automatización, seis casos y una falla documentada?** Usa la [fast lane de 30–45 minutos](docs/ruta-critica-antes-de-s2.md) dentro de la misma ruta. Si no, empieza por el Paso 0.

### Paso 0 — Abre tu copia

Crea tu copia privada con **Use this template** o abre la copia que ya tienes. Entra a la carpeta con Claude Code o Cowork. **No instales nada adicional todavía.**

### Paso 1 — Mira el ejemplo común

Abre [`ejemplo/README.md`](ejemplo/README.md) y lee solo estas dos secciones:

- **Problema**
- **La secuencia que enseña**

El camino dorado es un caso común de solicitudes que van a soporte, ventas, facturación o revisión humana. **No es un producto que tengas que construir:** es el ejemplo que usaremos para aprender el criterio.

### Paso 2 — Identifica qué ocurre en cada etapa

Antes de ejecutar nada, responde en una nota:

1. ¿Qué se resuelve con un `if`?
2. ¿Cuándo entra la IA?
3. ¿Dónde se valida la salida?
4. ¿Cuándo decide una persona?

### Paso 3 — Ejecuta el ejemplo offline

En macOS/Linux:

```bash
python3 ejemplo/camino_dorado.py --modo offline --version v1
```

En Windows:

```powershell
py ejemplo/camino_dorado.py --modo offline --version v1
```

Si no tienes Python, abre [`ejemplo/casos.json`](ejemplo/casos.json), recorre los seis casos núcleo con el diagrama y anótalos en una tabla. **No necesitas API key ni conexión a una API.**

### Paso 4 — Comprueba que entendiste

Escribe una respuesta breve para estas preguntas:

- ¿Qué casos no llegan a la IA?
- ¿Qué hace la IA cuando sí entra?
- ¿Qué pasa si la salida no valida?
- ¿Por qué un caso termina en humano?
- ¿Qué mejora `v1` respecto a `v0`?

### Paso 5 — Ahora sí, define tu foco

En Claude Code o Cowork, pega esto:

```text
Lee CLAUDE.md, ACOMPANAMIENTO.md y docs/ruta-critica-antes-de-s2.md.
Hazme una pregunta a la vez.
Ayúdame a elegir un solo proceso o caso.
No avances hasta que pueda explicar if, IA, validación y humano.
No inventes mis salidas esperadas.
```

### Paso 6 — Prepara tu llegada a S2

Fija **una decisión de IA**, seis casos —4 típicos, 1 límite y 1 adversarial—, la salida esperada de cada caso y un fallback.

Llegas listo(a) si puedes enseñar: **proceso/caso · una decisión · seis casos · salidas esperadas · fallback**.

➡️ Cuando termines, usa la [Ruta crítica antes de S2](docs/ruta-critica-antes-de-s2.md) como checklist completo.

## Objetivo

Este repositorio te acompaña para:

1. decidir qué automatizar y qué no, con evidencia;
2. separar lo que debe ser `if`, IA, herramienta o humano;
3. medir un sistema con casos reales y salida esperada;
4. diagnosticar si la falla está en el modelo, el contexto, el harness o la herramienta;
5. gobernar permisos, costos, aprobaciones y recuperación;
6. dejar un sistema que otra persona pueda operar sin ti.

La pregunta que guía todo el curso es:

> **Si mañana no estás, ¿alguien más puede correr el sistema, saber si funcionó y saber qué hacer si no?**

## Autoría y herramientas

**La dirección pedagógica, el diseño del curso, la doctrina y las decisiones finales de este repositorio son de León Ruiz.**

Claude Code y Cowork son **herramientas y asistentes de ejecución bajo su dirección**. No son coautores del repositorio. El criterio final, el alcance y la responsabilidad del material pertenecen a su autor y facilitador.

## Para quién es

| Perfil | Qué obtiene |
|---|---|
| Ya tienes automatizaciones y quieres productificarlas o escalarlas | Un marco para medir, endurecer, gobernar y entregar tu sistema. |
| Eres autodidacta o intermedio y ya sabes construir cosas | Una ruta que parte de tu experiencia y te pide la evidencia que falta, sin explicarte lo que ya sabes. |
| Eres avanzado | Un núcleo común y extensiones de costos, harness, MCP, loops y multiagente. |
| Todavía no tienes proyecto propio | Un camino dorado común para aprender el criterio antes de transferirlo a tu proceso. |

No es un chatbot de curso ni una lista de tutoriales. Es una infraestructura de trabajo para pasar del proceso al sistema y del sistema al producto.

## Elige tu puerta de entrada

| Soy… | Empiezo por… | Resultado inicial |
|---|---|---|
| Aprendedor(a) | [`Ruta crítica antes de S2`](docs/ruta-critica-antes-de-s2.md) | Una decisión acotada y seis casos núcleo |
| Facilitador | [`facilitador/README.md`](facilitador/README.md) | Agenda, preguntas, rescates y extensiones |
| Aprendedor(a) avanzado(a) | Ruta crítica + fast lane | Más profundidad sin repetir el onboarding |
| Sin entorno listo | [`ejemplo/README.md`](ejemplo/README.md) | Camino dorado offline o en papel |

> Si algo falla, consulta [`Dependencias y preflight`](docs/dependencias-y-preflight.md) como referencia secundaria. No instales Node/NPM si tu ruta no los necesita.

## Si todavía no vas a S2: primeros 15 minutos

1. Crea tu copia privada con **Use this template** y clónala, o trabaja en la copia que ya tienes.
2. Abre la carpeta en Claude Code o Cowork.
3. Lee [`Empieza aquí como Aprendedor(a)`](ALUMNO-EMPIEZA-AQUI.md) para orientación ampliada.
4. Si no tienes entorno listo, abre el [`Camino dorado`](ejemplo/README.md) sin credenciales.

No necesitas leer todo el repo, conectar una API real, usar n8n ni construir un agente autónomo para empezar.

## Ruta del curso

```text
proceso → decisión → evals → diagnóstico → límites → handoff
```

| Sesión | Pregunta central | Evidencia |
|---|---|---|
| S2 — Evals | ¿Cómo sé si mi decisión funciona? | Seis casos: 4 típicos, 1 límite y 1 adversarial; salida esperada y línea base |
| S3 — Loops | ¿Qué capa está fallando y necesito iteración real? | Diagnóstico, checker o cuatro paradas, traza y comparación v0 → v1 |
| S4 — Gobernanza | ¿Puede otra persona operar esto con límites claros? | Permisos, costo, aprobación, observabilidad, demo y handoff |
| S5 — Multiagente | ¿La complejidad adicional está justificada? | Extensión opcional para quien terminó el núcleo |

Los **6 casos** son el requisito mínimo válido. Los **10 casos** son una suite extendida para profundizar, no una condición para avanzar.

## Mapa del recorrido

![Mapa visual del curso: Aprendedor(a), evals, diagnóstico, gobernanza y handoff](docs/visuales/mapa-del-curso.png)

Fuente editable: [`docs/visuales/mapa-del-curso.mmd`](docs/visuales/mapa-del-curso.mmd).

## Camino dorado

El camino dorado ofrece un caso común antes de pedirte transferir el criterio a tu automatización:

```text
entrada → if determinista → IA solo si hay ambigüedad → salida estructurada → validación → humano
```

Puedes correrlo sin credenciales:

```bash
python3 ejemplo/camino_dorado.py --modo offline --version v1
```

| Versión | Núcleo | Extendida |
|---|---:|---:|
| `v0` | 4/6 — línea base intencional | 7/10 |
| `v1` | 6/6 | 10/10 |

Si no tienes Python, abre [`ejemplo/casos.json`](ejemplo/casos.json) y recorre los seis casos en papel. El contrato y las preguntas de diseño son los mismos.

## Comandos

| Comando | Qué hace |
|---|---|
| `/rumbo` | Assessment de entrada: qué quieres construir, qué puedes demostrar y qué ruta te conviene |
| `/arrancar` | Lleva un proceso al diseño de una automatización |
| `/eval` | Corre tus evals contra el sistema y devuelve una tasa |
| `/cuatro-paradas` | Diseña y ejecuta un loop con trabajo, verificación, parada y escalamiento |
| `/auditar` | Revisión crítica: identifica riesgos, contradicciones y teatro |
| `/verificar` | Re-verifica referencias sensibles contra fuentes oficiales |

Fuera de los comandos, habla normal con el asistente de ejecución. Pídele código, discute decisiones y conserva lo importante en disco.

## Qué hay en este repositorio

```text
README.md             esta portada y las puertas de entrada
ALUMNO-EMPIEZA-AQUI.md guía de primeros 15 minutos
docs/competencias.md   mapa de competencias de salida
docs/ruta-critica-antes-de-s2.md preparación accionable para S2
docs/dependencias-y-preflight.md matriz de dependencias por ruta y sistema operativo
CLAUDE.md             instrucciones del asistente bajo tu dirección
ACOMPANAMIENTO.md     cómo cambia el acompañamiento según tu evidencia
facilitador/          checklist, guiones S2–S4, rescates y debrief
curso/                ruta de cohorte y guías de sesión
ejemplo/              camino dorado, dataset y pruebas reproducibles
proyectos/            plantillas, rúbrica, demo y handoff
patrones/             siete patrones de automatización
referencias/          hechos verificados y fechados
docs/                 instalación, doctrina, seguridad y visuales
verificar.py          validación local de pruebas, fixtures, tasas y enlaces
.github/workflows/    validación automática en cada push y pull request
```

## Cómo te acompaña

El nivel de evidencia que demuestras en `/rumbo` decide cómo se te acompaña:

| Nivel | Modo | Qué hace |
|---|---|---|
| 0–1 | Enseñar | Explica el mecanismo en corto, con un ejemplo y una sola pregunta |
| 2 | Retar | Pide la evidencia que falta: número, archivo o criterio |
| 3 | Revisar como par | Señala riesgos y contradicciones; tú conduces |

La verdad de las salidas esperadas, umbrales y límites la fija la persona que conoce la operación. El asistente propone borradores; no inventa la verdad.

## Doctrina

- **Si puedes escribirlo como un `if`, que sea un `if`.**
- **Diseña la falla, no el éxito.**
- **Salida estructurada o no hay sistema.**
- **El harness importa más que el modelo.**
- **La condición de parada debe ser verificable sin el modelo.**

La versión completa está en [`docs/doctrina.md`](docs/doctrina.md) y [`CLAUDE.md`](CLAUDE.md).

## Verificación local

Antes de clase o antes de compartir cambios, ejecuta:

```bash
PYTHONDONTWRITEBYTECODE=1 python3 verificar.py
```

La verificación cubre pruebas reproducibles, fixtures de `/rumbo`, tasas del camino dorado, enlaces locales y whitespace de Git.

## Hechos y fechas

Los archivos de [`referencias/`](referencias/) están verificados al 9 de octubre de 2026 para Claude API, MCP, n8n, OKF, METR y multiagente; LangChain, harness y gobernanza están fechados al 13 de julio de 2026.

El conocimiento se pudre. Corre `/verificar` cada dos meses o antes de tomar una decisión de costos que importe. Para hechos sensibles a fecha, usa siempre la fuente oficial.

## Créditos y licencia

[MIT](LICENSE) © 2026 León Ruiz. Curso Productividad con Claude (IA) AVANZADO, [Collective Academy](https://collectiveacademy.com/). Basado en [ai-automation-expert](https://github.com/nabolom/ai-automation-expert) (Q3 2026).

Ilustración de portada: [Raúl Sisniega](https://www.behance.net/biosisniega) ©. Publicada con autorización del autor.
