## Seguridad

Nunca subas credenciales. `.gitignore` ya bloquea `.env`, y `.claude/settings.json` le prohíbe al agente leer `.env`, `.env.*`, `secrets/` y cualquier `credentials.json`.

Esas reglas cubren las herramientas de archivos del agente. Para lo que corre por terminal, activa el sandbox: escribe `/sandbox` dentro de Claude Code (macOS, Linux y WSL2; la doc lo recomienda para contener los comandos de shell: https://code.claude.com/docs/en/sandboxing).

Si tu proceso toca datos sensibles de tu empresa, lee `.claude/skills/seguridad-datos/SKILL.md` antes de conectar nada.
