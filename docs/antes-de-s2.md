## Antes de S2: /rumbo

> **Ruta recomendada para el grupo:** [`Ruta crítica antes de S2`](ruta-critica-antes-de-s2.md), de 60–90 minutos. Este archivo conserva los pasos técnicos del assessment `/rumbo`.

Antes de la segunda sesión, cada Aprendedor(a) corre el assessment de entrada. Fija qué va a construir, mide con evidencia dónde está y decide su ruta. No se enseña: se mide. El assessment mínimo toma unos 35 minutos; la preparación completa añade camino dorado, decisión y casos núcleo.

**Caso 1 · Vas a empezar tu repo hoy:**

1. Entra a https://github.com/nabolom/agentic-ai-automation-mentor-agent-2026 y usa "Use this template" → "Create a new repository", márcalo como Private y créalo.
2. Clónalo en tu computadora, entra a la carpeta y abre Claude Code con `claude`.
3. Escribe `/rumbo`.

**Caso 2 · Ya tienes tu repo del curso (creado desde ai-automation-expert):**

1. En la terminal, parado en tu repo, trae el assessment y la capa de acompañamiento:

   ```bash
   mkdir -p .claude/skills/rumbo
   curl -o .claude/skills/rumbo/SKILL.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/.claude/skills/rumbo/SKILL.md
   curl -o ACOMPANAMIENTO.md https://raw.githubusercontent.com/nabolom/agentic-ai-automation-mentor-agent-2026/main/ACOMPANAMIENTO.md
   echo "@ACOMPANAMIENTO.md" >> CLAUDE.md
   ```

2. Cierra y vuelve a abrir Claude Code, y escribe `/rumbo`.

**En ambos casos:**

1. Haz commit de tu `rumbo.md` y entrega su frontmatter a León 48 horas antes de S2.
2. Lleva a S2 lo que dice la sección "Qué llevo a S2" de tu `rumbo.md`.
