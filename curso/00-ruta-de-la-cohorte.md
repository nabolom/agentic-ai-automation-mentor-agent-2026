# Ruta de la cohorte

Esta ruta convierte el repositorio en una experiencia de tres sesiones de 2.5 horas. La doctrina sigue viviendo en `CLAUDE.md`; este archivo responde una pregunta distinta: **¿qué hacemos en clase, en qué orden y qué queda listo?**

## Resultado del curso

Al terminar, cada Aprendedor(a) debe poder tomar una automatización real y responder con evidencia:

1. **Qué parte es una regla, qué parte necesita IA y qué parte debe seguir siendo humana.**
2. **Cómo sabe que el sistema terminó bien sin preguntarle al modelo.**
3. **Cuánto acierta sobre una suite de casos conocidos.**
4. **Qué ocurre cuando falla, se sale de alcance o intenta una acción irreversible.**
5. **Cómo lo corre otra persona sin depender del autor.**

No es obligatorio construir un agente autónomo. **Justificar un workflow con un solo paso de IA, o decidir no automatizar todavía, también es un resultado válido.**

El mapa completo de salida está en [`Competencias de Agentic AI`](../docs/competencias.md). La preparación inmediata para S2 está en la [`Ruta crítica antes de S2`](../docs/ruta-critica-antes-de-s2.md).

## Cómo trabajarás

Hay dos rutas de implementación, con los mismos criterios de calidad:

| Ruta | Úsala si… | Debes demostrar |
|---|---|---|
| **Visual** | Tu automatización vive en n8n, Make, CoWork u otra herramienta visual | Flujo, entradas/salidas, validación, evals y guardrails |
| **Código/API** | Quieres trabajar con Claude Code, Python, TypeScript o una API directa | Contrato de entrada/salida, validación, pruebas, errores y límites |

La herramienta cambia. **El contrato no cambia.** Ambas rutas deben producir una salida estructurada, una suite de casos y un criterio de escalamiento.

## Núcleo y extensión

### Núcleo: todas las personas

- Un proceso acotado o el caso común del `ejemplo/`.
- Una sola decisión de IA.
- Seis casos: cuatro típicos, uno límite y uno adversarial. **Es una medición válida, no una suite incompleta.**
- Una salida esperada fijada por la persona.
- Un análisis de un fallo.
- Un criterio de éxito verificable.
- Una matriz mínima de permisos, escalamiento y observabilidad.

### Extensión: para quien termina antes

- Suite extendida de diez casos: cinco típicos, tres límite y dos adversariales.
- Calibración de `confianza` por categoría.
- Corrida end-to-end con datos reales anonimizados.
- Costo por corrida y proyección mensual.
- Loop con cuatro paradas, solo si el flujo realmente itera.
- S5, multiagente: comparación de agente único contra Nest o Swarm. Es extensión avanzada, no requisito común.

La extensión no se usa para avanzar más rápido el calendario ni para convertir el núcleo en una carrera.

## Preflight antes de clase

La preparación previa vive en la [Ruta crítica antes de S2](../docs/ruta-critica-antes-de-s2.md). No repitas aquí la instalación: elige ruta, verifica solo sus dependencias y conserva un fallback.

Si algún paso falla, lleva la captura o el mensaje de error; **no intentes resolverlo durante los primeros minutos de clase**. El camino dorado offline o en papel conserva el aprendizaje sin credenciales reales.

## Sesión 2 — De automatización a sistema medible

Esta es la sesión que recupera el puente perdido de la primera clase. No intenta reconstruir toda la teoría: usa el camino dorado para recordar el vocabulario y deja un caso acotado listo para medir. Si ya tienes un proceso, puedes saltar del ejemplo común al tuyo; si no, termina la sesión con el caso común.

Consulta también la [guía completa de S2](S2-evals.md).

**Objetivo:** salir con un caso acotado, una decisión de IA y una primera medición.

| Tiempo | Actividad | Checkpoint |
|---:|---|---|
| 0–15 min | Recuperación: clasificar pasos como `if`, IA, herramienta o humano | Cada persona explica una decisión |
| 15–35 min | Demo del camino dorado, incluido un caso que escala | Se identifica dónde no debe decidir el modelo |
| 35–55 min | Elegir un proceso propio o usar el caso común | Un solo proceso, no dos |
| 55–80 min | Mapear el flujo actual y definir “terminado” | `flujo.md` y `alcance.md` |
| 80–100 min | Diseñar una sola decisión de IA | Contrato de salida |
| 100–120 min | Fijar seis evals | Salida esperada escrita antes de correr |
| 120–140 min | Correr la línea base | Tasa + salida cruda |
| 140–150 min | Diagnosticar un fallo y cerrar | Causa probable + exit ticket |

**Entregable:** `proyecto.md`, `flujo.md`, `alcance.md`, `decisiones.md`, `reglas.md` y `evals.md` con seis casos.

**Evidencia, no solo archivos:** la tasa `aciertos/6` con su modo (escritorio), la salida cruda de al menos un caso fallido y una línea con la causa probable.

## Sesión 3 — Fallas, verificación y loops

Consulta también la [guía completa de S3](S3-loops.md).

**Objetivo:** distinguir una falla del modelo de una falla de contexto, herramienta o harness.

| Tiempo | Actividad | Checkpoint |
|---:|---|---|
| 0–15 min | Recuperación de la línea base | Comparar número y casos fallidos |
| 15–40 min | Diagnóstico por capas y harness | Nombrar la capa rota y la evidencia |
| 40–55 min | Decidir si hace falta un loop | “No necesito loop” es una salida válida, con su razón escrita |
| 55–85 min | Con loop: `/cuatro-paradas` con números. Sin loop: escribir la verificación externa del paso | Cuatro paradas con números, o un checker que no le pregunta al modelo |
| 85–105 min | Correr una traza, o la suite con el checker | Trabajo y verificación separados |
| 105–135 min | Aplicar un solo ajuste (v0 → v1) y volver a correr `/eval` | Número antes y después |
| 135–150 min | Guardar evidencia y cerrar | `diagnostico.md`, `harness.md`, `evals.md` con v1 y, si aplica, `loop.md` |

**Entregable:** diagnóstico de una falla, una verificación externa y una mejora medida. Solo hay `loop.md` si el flujo realmente necesita iterar.

**Evidencia, no solo archivos:** la capa nombrada con lo que descartó las otras, la comparación v0 → v1 sobre los mismos seis casos, y la traza o la corrida del checker.

## Sesión 4 — Gobernanza, handoff y defensa

Consulta también la [guía completa de S4](S4-gobernanza.md).

**Objetivo:** que otra persona pueda operar el sistema con límites claros.

| Tiempo | Actividad | Checkpoint |
|---:|---|---|
| 0–20 min | Recuperación sobre permisos y acciones irreversibles | Identificar el mayor riesgo |
| 20–45 min | `/auditar`: encontrar el teatro | Los tres hallazgos que más duelen (de máximo cinco) |
| 45–75 min | Permisos mínimos y tope de gasto | Matriz de gobernanza |
| 75–100 min | Human-in-the-loop y Error Trigger | Acción irreversible y señal de falla |
| 100–120 min | Corrida end-to-end con `/eval` | Tasa del sistema, no solo del prompt |
| 120–140 min | Una mejora guiada por evidencia | Comparación antes/después |
| 140–150 min | Demo por parejas y handoff | Preguntas de defensa respondidas |

**Entregable final:** paquete de ejecución con README corto, evals, evidencia de una corrida, gobernanza, limitaciones y qué hacer si falla.

**Evidencia, no solo archivos:** la tasa del sistema en modo sistema (o `BLOQUEADO` con lo que falta), una falla provocada y cómo te enteraste, y tu pareja corriendo una prueba con tu handoff sin ayuda.

## Si algo falla en clase

| Falla | No hagas | Haz esto |
|---|---|---|
| No instala Claude Code | Convertir la clase en soporte técnico | Usa el camino dorado offline |
| Tampoco hay Python | Esperar a que alguien lo instale | Recorre el camino dorado en papel con `ejemplo/casos.json` |
| `/eval` no corre | Inventar la tasa | Corre los casos en tu herramienta o a mano y cuenta contra la salida esperada |
| No autentica una API | Pegar una llave en un archivo | Usa datos sintéticos y deja el punto de integración documentado |
| No existe un proceso real | Inventar una línea base | Trabaja el caso común y marca la transferencia como siguiente paso |
| La herramienta visual no responde | Cambiar de plataforma a mitad de sesión | Completa el contrato y los evals con el formato local |
| Agent Teams no arranca | Depurarlo durante el taller | Usa la conclusión preparada y discute el juicio arquitectónico |

## Criterio de salida

No se evalúa cuántos comandos ejecutaste. Se evalúa si puedes defender estas cinco respuestas:

1. ¿Dónde usas IA y por qué no un `if`?
2. ¿Qué caso te da más miedo?
3. ¿Cómo sabes que funcionó sin preguntarle al modelo?
4. ¿Qué acción nunca dejarías automática?
5. Si tú desapareces mañana, ¿quién lo corre?
