## Seguridad

Nunca subas credenciales. `.gitignore` ya bloquea `.env`, y `.claude/settings.json` le prohíbe al agente leer `.env`, `.env.*`, `secrets/` y cualquier `credentials.json`.

Esas reglas cubren las herramientas de archivos del agente; **no son una frontera completa de seguridad**. Para los comandos que corren por terminal, activa el sandbox escribiendo `/sandbox` dentro de Claude Code y revisa las plataformas compatibles en la [documentación oficial](https://code.claude.com/docs/en/sandboxing) antes de diseñar el ejercicio.

El sandbox también necesita límites de red y de escritura razonables. No amplíes allowlists sin revisar qué capacidad adicional le otorgas al agente.

Si tu proceso toca datos sensibles de tu empresa, lee `.claude/skills/seguridad-datos/SKILL.md` antes de conectar nada.
