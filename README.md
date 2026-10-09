# Agentic AI & Automation Mentor Agent 2026

Tu experto en construcción de productos de IA y automatizaciones, dentro de Claude Code.

No es un chatbot de curso. Es infraestructura: la clonas una vez y te sirve para la automatización #1 y para la #12, seis meses después de que el curso terminó. Y antes de la segunda sesión te hace una pregunta incómoda: ¿qué vas a construir, y qué puedes demostrar hoy?

**Curso Productividad con Claude (IA) AVANZADO — Collective Academy, Q4 2026.**

Basado en [ai-automation-expert](https://github.com/nabolom/ai-automation-expert), la versión de Q3 2026.

---

## Arranque

### Paso 1 — Instala Claude Code

El método principal es el **instalador nativo**. No necesita Node ni npm.

**macOS, Linux y WSL:**

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**Windows (PowerShell):**

```powershell
irm https://claude.ai/install.ps1 | iex
```

Cierra y vuelve a abrir la terminal, y verifica:

```bash
claude --version
```

Debe devolver un número de versión. Si dice `command not found`, el directorio de instalación no está en tu PATH todavía: sigue la guía oficial en https://code.claude.com/docs/en/setup (sección *Fix your PATH*).

**Alternativa con npm** (solo si ya vives en Node; requiere Node 22 o superior):

```bash
npm install -g @anthropic-ai/claude-code
```

Necesitas también **Git** (`git --version`). En macOS viene con las Command Line Tools (`xcode-select --install`); en Windows, desde [git-scm.com](https://git-scm.com/download/win).

Claude Code requiere una cuenta Pro, Max, Team, Enterprise o de Console. Al correr `claude` por primera vez te pide iniciar sesión en el navegador.

### Paso 2 — Crea tu copia del repo

**No hagas fork ni clones directo.** Usa el botón de template para tener tu propio repo con permisos de escritura:

1. Ve a [github.com/nabolom/agentic-ai-automation-mentor-agent-2026](https://github.com/nabolom/agentic-ai-automation-mentor-agent-2026)
2. Click en el botón verde **“Use this template”** → **“Create a new repository”**
3. Pon el nombre que quieras (ej. `mi-automatizacion`)
4. Márcalo como **Private** — tus procesos de negocio no tienen por qué ser públicos
5. Click en **“Create repository”**

Ahora clona **tu** repo (el que acabas de crear, no el mío). `git clone` crea la carpeta **donde estés parado en la terminal**; corre `pwd` si no sabes dónde estás.

```bash
mkdir ~/proyectos-ia && cd ~/proyectos-ia
git clone https://github.com/TU-USUARIO/TU-REPO.git
cd TU-REPO
claude
```

Al entrar al directorio y correr `claude`, el agente lee automáticamente `CLAUDE.md` y carga la doctrina, el mapa del repo, las skills y la capa de acompañamiento. No necesitas configurar nada más.

Los repos creados desde template **no reciben actualizaciones automáticas**: son una foto del día que los creaste. Cada sesión del curso trae su propio paso para traer lo nuevo con `curl`.

### Paso 3 — Arranca tu primera automatización

Dentro de Claude Code, escribe:

```
/arrancar
```

El agente te va a conducir paso a paso: elegir un proceso, mapearlo, clasificar cada paso, identificar el patrón, medir la línea base y definir el alcance. Al terminar tendrás cinco archivos de tu proyecto en `proyectos/`. O un veredicto honesto de "no automatizar todavía", que también cuenta.

---

## Comandos

| Comando | Qué hace |
|---|---|
| `/rumbo` | Assessment de entrada: qué vas a construir, qué puedes demostrar hoy, y tu ruta |
| `/arrancar` | Nueva automatización: del proceso al diseño |
| `/eval` | Corre tus evals contra el prompt actual y te da la tasa de acierto |
| `/cuatro-paradas` | Diseña y ejecuta un loop de trabajo-verificación con cuatro paradas explícitas (antes `/loop`) |
| `/auditar` | Revisión crítica. Te dice qué parte de tu sistema es teatro |
| `/verificar` | Re-verifica las referencias contra fuente oficial |

Fuera de los comandos, habla normal. Pregúntale, pídele código, discútele decisiones. Tiene el contexto.

---

## Estructura

```
CLAUDE.md             el cerebro
ACOMPANAMIENTO.md     cómo te acompaña según lo que demostraste en /rumbo
rumbo.md              tu assessment (lo genera /rumbo)
.claude/commands/     los comandos de arriba
.claude/skills/       capacidades — se cargan bajo demanda
.claude/settings.json permisos: el agente no lee .env ni secretos
patrones/             los siete patrones, con estructura y trampas
referencias/          hechos verificados y FECHADOS ← lo más valioso
proyectos/            tus automatizaciones
curso/                las guías de cada sesión
```

---

## Por qué este repo existe

Un asistente de IA genérico ya sabe qué es un webhook. Lo que **no** tiene es criterio, hechos frescos y patrones probados. Y peor: **alucina precios, rate limits y nombres de nodos con total confianza.**

Tres cosas viven aquí, y solo tres:

**1. Doctrina.** Opiniones, no análisis balanceados. Preguntas "¿agente o workflow?" y obtienes una respuesta, con el criterio para decidirlo tú la próxima vez.

**2. Hechos verificados y fechados.** Precios, rate limits, versiones, nombres exactos de nodos — contra fuente oficial, con fecha. Cuando el asistente y la referencia se contradigan, **gana la referencia**.

`referencias/` es un bundle conforme a **Open Knowledge Format** (el spec que Google Cloud publicó en junio de 2026 para formalizar el patrón "LLM wiki"; hoy va en v0.2). Portable, interoperable, y crece solo: el agente puede escribir conceptos nuevos cuando aprende algo.

**3. Patrones ejecutables.** Siete formas. Casi toda automatización de negocio es una de ellas.

---

---

## La doctrina, en corto

1. **Si puedes escribirlo como un `if`, que sea un `if`.** La IA es cara, lenta y no determinista.
2. **¿Puedes dibujar el diagrama completo?** Entonces es un workflow, no un agente.
3. **Diseña la falla, no el éxito.** Nadie está viendo a las 3 AM.
4. **Salida estructurada o no hay sistema.** JSON con esquema, validado.
5. **Los prompts son código.** Versiónalos, corre evals cuando cambien.
6. **Un sistema completo a medias > medio sistema completo.**
7. **El agente debe saber cuándo no sabe.** Escalamiento explícito.
8. **Mide el proceso antes de automatizarlo.** No se recupera después.
9. **Lo que no está en disco no existe.**
10. **El harness importa más que el modelo.** Antes de subir de modelo, arregla el andamio.
11. **La condición de parada debe ser verificable sin el modelo.** Un modelo siempre cree que avanzó.
12. **El conocimiento vive en archivos, no en prompts.** Un concepto por archivo, versionado junto al código (OKF).
13. **Menos pasos, siempre.** `0.95^20 = 0.358`. Veinte pasos al 95% y el sistema funciona el 36% de las veces.
14. **Cuando falle, pregunta qué CAPA está rota.** Casi nunca es el modelo. Ver `referencias/agent-engineering.md`.

¿Sabes hacer las ocho cosas que separan una demo de un sistema? → [`COMPETENCIAS.md`](COMPETENCIAS.md)

---

---

## Los siete patrones

| # | Patrón | Pieza clave |
|---|---|---|
| 01 | Clasificar y rutear | Text Classifier — **no un agente** |
| 02 | Extraer documento → JSON | Information Extractor |
| 03 | Human-in-the-loop | Chat node / HIL en tool calls |
| 04 | RAG interno | Vector store + citas obligatorias |
| 05 | Watcher | Estado + umbral de relevancia |
| 06 | Enriquecer datos | Batch API (50% menos) |
| 07 | Loop agéntico de larga duración | Harness: progreso + verificación externa |

---

---

## Advertencia sobre los hechos

Los archivos de `referencias/` están verificados al **9 de octubre de 2026** (Claude API, MCP, n8n, OKF, METR, multiagente; LangChain, harness y gobernanza al 13 de julio de 2026).

Se pudren. Corre `/verificar` cada dos meses, o antes de cualquier decisión de costos que importe.

Al armar este repo, tres de los blogs mejor rankeados de "Claude API pricing 2026" tenían datos viejos o mal — incluyendo el primer resultado de Google. **Siempre la fuente oficial.**

---

## Seguridad

Nunca subas credenciales. `.gitignore` ya bloquea `.env`, y `.claude/settings.json` le prohíbe al agente leer `.env`, `.env.*`, `secrets/` y cualquier `credentials.json`.

Esas reglas cubren las herramientas de archivos del agente. Para lo que corre por terminal, activa el sandbox: escribe `/sandbox` dentro de Claude Code (macOS, Linux y WSL2; la doc lo recomienda para contener los comandos de shell: https://code.claude.com/docs/en/sandboxing).

Si tu proceso toca datos sensibles de tu empresa, lee `.claude/skills/seguridad-datos/SKILL.md` antes de conectar nada.

---

## Sesiones del curso

| Sesión | Guía |
|---|---|
| S2 — Evals: mide tu decisión de IA | [`curso/S2-evals.md`](curso/S2-evals.md) |
| S3 — Loops: el sistema que corre solo y para solo | [`curso/S3-loops.md`](curso/S3-loops.md) |
| S4 — Gobernanza: qué pasa cuando se rompe a las 3 AM | [`curso/S4-gobernanza.md`](curso/S4-gobernanza.md) |
| S5 — Multiagente a juicio | [`curso/S5-multiagente.md`](curso/S5-multiagente.md) · ejercicio: [`curso/EJERCICIO-S5.md`](curso/EJERCICIO-S5.md) |
