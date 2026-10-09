## Sesión 4 — Gobernanza: qué pasa cuando se rompe a las 3 AM

En la Sesión 1 diseñaste el sistema. En la 2 mediste su decisión de IA. En la 3 lo hiciste **correr solo**. La Sesión 4 hace la pregunta que decide si eso vive en producción o se cae el martes: **¿qué pasa cuando falla y nadie está viendo?**

Un loop que corre solo, sin gobernanza, no es un sistema — es un riesgo con buena demo. Manda el correo antes de que alguien lo apruebe. Gasta sin techo. Y cuando falla, la falla es invisible. Hoy le pones los guardrails que le faltan, y —por primera vez— sacas su **tasa de acierto real**: no la de escritorio de la Sesión 2, sino la del sistema corriendo end-to-end.

La idea central viene de la doctrina (`CLAUDE.md` §3, §7, §13) y de lo que Anthropic aprendió conteniendo a Claude en producción (`referencias/gobernanza.md`): **el límite duro va en el entorno, no en el prompt.** El modelo es probabilístico; nunca es la última línea de defensa.

Dos hechos que lo aterrizan, ambos verificados:

- La telemetría de Claude Code mostró que los usuarios aprobaban **~93%** de los prompts de permiso — sin leerlos. El human-in-the-loop en cada paso **no escala**: se vuelve un clic reflejo. Resérvalo para lo irreversible.
- En un red-team interno (feb 2026), un prompt malicioso logró que el agente exfiltrara credenciales **24 de 25 veces**. La instrucción llegó *tecleada por el usuario*, así que no había nada anómalo que un clasificador atrapara. Lo único que la habría detenido: el entorno — egress y límites de archivo.

Gobernar no es enumerar cada acción mala. Es **acotar lo que el sistema puede alcanzar**. Cuatro palancas, y hoy configuras las cuatro:

| # | Palanca | La pregunta que responde |
|---|---|---|
| 1 | **Permisos mínimos** | ¿Qué es lo mínimo que necesita tocar — y por qué no más? |
| 2 | **Tope de gasto** | ¿Cuánto puede gastar antes de que alguien lo detenga? |
| 3 | **Human-in-the-loop** | ¿Qué acción irreversible NO se dispara sin un humano? |
| 4 | **Observabilidad** | Cuando falle, ¿cómo me entero — hoy, no en el reporte del mes? |

---

### Paso 0 — Trae `PLANTILLA-gobernanza.md` a TU repo 📍 EN LA TERMINAL

`/auditar` ya lo tienes (es comando base, viene desde que creaste tu repo). Lo único nuevo de esta sesión es la plantilla. Parado en tu repo (`pwd` para ubicarte, `cd` a tu carpeta):

```bash
ls proyectos/     # ¿ya aparece PLANTILLA-gobernanza.md?
```

Si aparece, salta al Paso 1. Si NO, tráela:

```bash
curl -o proyectos/PLANTILLA-gobernanza.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/proyectos/PLANTILLA-gobernanza.md
```

Confirma que `/auditar` sí está y guarda la plantilla:

```bash
ls .claude/commands/          # debe aparecer auditar.md
ls proyectos/                 # debe aparecer PLANTILLA-gobernanza.md

git add proyectos/PLANTILLA-gobernanza.md
git commit -m "sesion 4: plantilla de gobernanza"
git push
```

Si `auditar.md` NO aparece (creaste tu repo muy temprano), tráelo igual:

```bash
curl -o .claude/commands/auditar.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/.claude/commands/auditar.md
```

**Importante:** si Claude Code estaba abierto, ciérralo (`Ctrl+C`) y vuelve a entrar (`claude`).

---

### Paso 1 — Corre `/auditar`: qué parte de tu sistema es teatro 📍 EN CLAUDE CODE

No empieces tapando huecos al azar. Primero deja que la auditoría te diga **cuáles son**. Este comando no está para ayudarte — está para encontrar lo que un cliente encontraría primero.

```
/auditar
```

Lee todo tu `proyectos/<tu-proyecto>/` y te devuelve máximo cinco hallazgos, ordenados por lo que más te va a doler: dónde falta tope de gasto, qué acción irreversible corre sin humano, dónde no hay forma de enterarte de una falla, dónde pagas IA por algo que era un `if`. Queda escrito en `proyectos/<tu-proyecto>/auditoria-<fecha>.md`.

**Esa lista es tu plan de trabajo del resto de la sesión.** Cada hueco que encontró, lo cierras en los pasos que siguen.

```bash
git add proyectos/
git commit -m "sesion 4: auditoria - N huecos de gobernanza"
git push
```

---

### Paso 2 — Permisos mínimos y tope de gasto 📍 EN CLAUDE CODE

Copia la plantilla a tu proyecto y llena las dos primeras secciones:

```
cp proyectos/PLANTILLA-gobernanza.md proyectos/<tu-proyecto>/gobernanza.md
```

**Permisos mínimos (§1).** Por cada credencial o recurso que toca tu sistema: ¿es el mínimo que le permite trabajar? Solo-lectura donde se pueda. Un agente con acceso de solo-lectura se puede soltar mucho más ancho que uno que escribe a prod. Y la regla de la allowlist: cada dominio o API que permites no es un destino, es un **grant de capacidad** — anota qué puede hacer con cada uno.

**Tope de gasto (§2).** Un loop con API de pago es una factura sin techo hasta que le pones un número. Tres límites: gasto en la consola de tu proveedor, tokens por corrida, e iteraciones por corrida. Este último ya lo tienes: es la parada de *presupuesto* de tu `loop.md` de la Sesión 3 — cópiala aquí con el mismo número.

> El monto real y dónde se configura en la consola: **ábrela y verifícalo ahora**, no lo pongas de memoria. Ese número en tu commit es el entregable.

```bash
git add proyectos/
git commit -m "sesion 4: permisos minimos y tope de gasto"
git push
```

---

### Paso 3 — Human-in-the-loop y Error Trigger 📍 EN CLAUDE CODE

Aquí cierras las dos secciones que más pesan en la auditoría.

**Human-in-the-loop (§3).** No en cada paso — eso es el clic reflejo del 93%. Solo antes de lo **irreversible**: mandar, cobrar, borrar, publicar. Por cada una: ¿requiere aprobación?, ¿quién aprueba?, ¿por qué canal?, ¿qué ve antes de decir que sí? Esto extiende la tabla de escalamiento que ya escribiste en `loop.md` — no la dupliques, complétala.

**Error Trigger + observabilidad (§4).** Si no te enteras de que falló, no lo manejas. Por cada modo de falla (API caída, LLM fuera de esquema, presupuesto tocado, no-progreso): ¿cómo te enteras, por qué canal, con qué umbral? El mínimo viable es un disparador de error que mande una alerta a un canal que sí revisas.

```bash
git add proyectos/
git commit -m "sesion 4: human-in-the-loop y error trigger configurados"
git push
```

---

### Paso 4 — La tasa de acierto REAL 📍 EN CLAUDE CODE

El número de la Sesión 2 medía **un prompt**, en el escritorio. Ahora tu sistema corre solo, con guardrails. Córrelo end-to-end contra tus 10 evals y mide qué acierta **como sistema**:

```
/eval
```

Va a ser más baja que la de escritorio. Eso es lo correcto y lo honesto — un prompt de 9/10 puesto a correr solo pierde en las junturas: se queda sin contexto, declara terminado antes de tiempo, escala algo que no debía. Ese número real es lo que llevas al Demo Day. Anótalo como la primera traza real en tu `loop.md`.

```bash
git add proyectos/
git commit -m "sesion 4: tasa de acierto real del sistema - X/10"
git push
```

---

### Paso 5 — Mejora continua: arregla UNA cosa con evidencia 📍 EN CLAUDE CODE

Toma **un** eval que falló en la corrida real. No lo arregles a ojo — haz análisis de error: ¿por qué falló exactamente? ¿capa, dato, regla ambigua? (la escalera de la Sesión 2 sigue aplicando). Arregla el prompt, y **vuelve a correr `/eval`**:

```
/eval
```

Compara antes/después. Puede que subas el número — o que arregles ese caso y rompas otros dos. Cualquiera de las dos es la lección: **cada vez que tocas un prompt, corren los evals.** Esa es la disciplina que separa mejorar un sistema de rezarle. Desde hoy no toques un prompt sin correr la suite.

```bash
git add proyectos/
git commit -m "sesion 4: postmortem + fix con evals antes/despues"
git push
```

Al final de la noche tu `git log` cuenta la historia de la robustez: la auditoría → los permisos → los guardrails → el número real → la primera mejora medida. Eso es un sistema, no una demo.

---
