## Sesión 3 — Loops: el sistema que corre solo y para solo

En la Sesión 1 diseñaste el sistema. En la Sesión 2 mediste su decisión de IA. La Sesión 3 cierra el núcleo: **convertir el paso donde HOY el humano es el bucle** — revisar, corregir, volver a revisar — en un loop que trabaja, se verifica y se detiene sin que nadie lo esté viendo.

La idea central viene de la doctrina (`CLAUDE.md` §11): un loop sin condición de parada verificable no es automatización — es una fuga de presupuesto con un optimista adentro. Todo loop necesita **cuatro paradas**:

| # | Parada | La pregunta que responde |
|---|---|---|
| 1 | **Éxito** | ¿Cómo sabe que terminó BIEN — sin preguntarle al modelo? |
| 2 | **Presupuesto** | ¿Cuántas vueltas / cuánto dinero antes de rendirse? |
| 3 | **No-progreso** | ¿Cómo detecta que da vueltas sin avanzar? |
| 4 | **Escalamiento** | ¿Qué casos van a un humano ANTES de agotar presupuesto? |

Falta una y el loop es un riesgo (§11). Las cuatro con números concretos, o el loop no se escribe.

---

### Paso 0 — Trae `/cuatro-paradas` y su plantilla a TU repo 📍 EN LA TERMINAL

> Este comando se llamaba `/loop` en Q3. Se renombró porque Claude Code trae un `/loop` integrado (corre un prompt en intervalos) y los dos chocaban. Si en tu repo todavía tienes `.claude/commands/loop.md`, bórralo y trae el nuevo.

Igual que en la Sesión 2: tu repo es una foto del día que lo creaste, y `/cuatro-paradas` se publicó después. Parado en tu repo (`pwd` para ubicarte, `cd` a tu carpeta), verifica:

```bash
ls .claude/commands/
```

Si aparece `cuatro-paradas.md`, salta al Paso 1. Si NO, copia y pega estas dos líneas (cada una completa):

```bash
curl -o .claude/commands/cuatro-paradas.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/.claude/commands/cuatro-paradas.md
curl -o proyectos/PLANTILLA-loop.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/proyectos/PLANTILLA-loop.md
```

Confirma y guarda en tu repo:

```bash
ls .claude/commands/          # debe aparecer cuatro-paradas.md
ls proyectos/                 # debe aparecer PLANTILLA-loop.md

git add .claude/commands/cuatro-paradas.md proyectos/PLANTILLA-loop.md
git commit -m "sesion 3: comando /cuatro-paradas y plantilla de loops"
git push
```

**Importante:** si Claude Code estaba abierto, ciérralo (`Ctrl+C`) y vuelve a entrar (`claude`) — los comandos nuevos solo se detectan al arrancar.

---

### Paso 1 — Diagnostica antes de construir 📍 EN CLAUDE CODE

Antes de escribir un loop, nombra la capa donde tu sistema falla hoy. Un loop mal ubicado automatiza el paso equivocado.

Copia las dos plantillas a tu proyecto:

```
cp proyectos/PLANTILLA-diagnostico.md proyectos/<tu-proyecto>/diagnostico.md
cp proyectos/PLANTILLA-harness.md proyectos/<tu-proyecto>/harness.md
```

Si no las tienes todavía, tráelas igual que `/cuatro-paradas`:

```
curl -o proyectos/PLANTILLA-diagnostico.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/proyectos/PLANTILLA-diagnostico.md
curl -o proyectos/PLANTILLA-harness.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/proyectos/PLANTILLA-harness.md
```

**`diagnostico.md`** — toma los casos que fallaron en tu `evals.md` y clasifícalos por capa. La columna que cuesta es *evidencia*: «se siente como el modelo» no es evidencia; «le di el dato explícito y aun así falló» sí lo es. Nadie escribe «modelo» sin descartar las otras tres capas por escrito.

**`harness.md`** — inventario de las cuatro capas de tu sistema: qué existe, dónde vive, qué falta. Cada capa termina con al menos un hueco nombrado. Si no le falta nada a ninguna, tu sistema nunca ha corrido solo.

Las cuatro capas se diagnostican **de abajo hacia arriba** — harness, framework, contexto, modelo — porque lo barato y probable se revisa primero. El marco completo está en `referencias/harness.md`.

```
git add proyectos/
git commit -m "sesion 3: diagnostico por capas e inventario de harness"
git push
```

---

### Paso 2 — Corre `/cuatro-paradas` en tu proyecto 📍 EN CLAUDE CODE

**Prerequisitos:** `/cuatro-paradas` lee tu `flujo.md`, tu `evals.md` y tu `alcance.md`. Si falta alguno, el comando se detiene y te lo dice — las Sesiones 1 y 2 son el suelo de esta. Si tu suite de evals quedó incompleta, ciérrala primero (la [guía de evals](../proyectos/GUIA-escribir-evals.md) sigue ahí).

```
/cuatro-paradas
```

El comando trabaja en cinco fases, y te va a exigir números — no te aceptes a ti mismo respuestas cualitativas:

| Fase | Qué pasa | Tu papel |
|---|---|---|
| 1 | Identifica EL paso candidato de tu `flujo.md` (uno solo) | Confirmar o corregir |
| 2 | Te exige las cuatro paradas con valores concretos | Dar números: "máx 5 iteraciones o $8 MXN", no "las que necesite" |
| 3 | Escribe la especificación en `proyectos/<tu-proyecto>/loop.md` | Revisar que verificación y trabajo sean pasos SEPARADOS |
| 4 | Corre el loop UNA vez contra un caso real de tus evals | Mirar la traza que queda en `trazas/` |
| 5 | Te pregunta: ¿salió por donde esperabas? | Aplicar UN ajuste y volver a correr |

---

### Paso 3 — Lee la traza como diagnóstico 📍 EN CLAUDE CODE

La traza dice **por cuál de las cuatro paradas salió** el loop, y cada salida es un diagnóstico distinto:

| Salió por… | Significa |
|---|---|
| Presupuesto | Tu condición de éxito probablemente es inalcanzable, no estricta |
| No-progreso en la primera revisión | Tu verificación no está midiendo nada útil |
| Éxito en la primera vuelta | No necesitabas un loop — necesitabas un prompt |
| Escalamiento con un caso que SÍ estaba en alcance | Tu disparador está mal calibrado |

Un ajuste a la vez — el que más mueva la aguja. Corre de nuevo. Y commit después de cada corrida, porque la traza es evidencia: es lo que hace que la Sesión 4 pueda comparar contra algo en vez de empezar de cero.

```bash
git add proyectos/
git commit -m "loop: primera traza - salio por <parada>"
git push
```

---
