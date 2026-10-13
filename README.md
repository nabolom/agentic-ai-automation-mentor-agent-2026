# Agentic AI & Automation Mentor Agent 2026

[![Licencia: MIT](https://img.shields.io/badge/licencia-MIT-green.svg)](LICENSE)

Un mentor dentro de Claude Code que te lleva del proceso al sistema, y del sistema al producto.

## Menú

- [Objetivo](#objetivo)
- [Para quién es](#para-quién-es)
- [Empieza en 3 pasos](#empieza-en-3-pasos)
- [Empieza aquí como alumno](#empieza-aquí-como-alumno)
- [Tu ruta](#tu-ruta)
- [Comandos](#comandos)
- [Qué hay en este repo](#qué-hay-en-este-repo)
- [Cómo te acompaña](#cómo-te-acompaña)
- [Doctrina](#doctrina)
- [Hechos y fechas](#hechos-y-fechas)
- [Créditos y licencia](#créditos-y-licencia)

Guías: [Ruta de la cohorte](curso/00-ruta-de-la-cohorte.md) · [Camino dorado](ejemplo/README.md) · [Instalación](docs/instalacion.md) · [Antes de S2: /rumbo](docs/antes-de-s2.md) · [Doctrina en corto](docs/doctrina.md) · [Las 8 competencias](docs/competencias.md) · [Seguridad](docs/seguridad.md) · [Sesiones del curso](curso/README.md) · [Kit del facilitador](facilitador/README.md) · [Mapa visual](docs/visuales/mapa-del-curso.png) · [Los siete patrones](patrones/README.md)

Si vienes a la cohorte, empieza por la [Ruta de la cohorte](curso/00-ruta-de-la-cohorte.md) y ejecuta el [Camino dorado](ejemplo/README.md). El resto del repositorio funciona como referencia y mentoría bajo demanda.

## Objetivo

- Decidir qué automatizar y qué no, con evidencia.
- Medir tu sistema con un número y operarlo con cuatro paradas y gobernanza.
- Convertirlo en algo que otra persona corre sin ti.

La prueba de la ausencia: **si mañana no estás, ¿alguien más lo corre, sabe si funcionó y sabe qué hacer si no?**

## Para quién es

| Perfil | Qué obtienes |
|---|---|
| Ya tienes automatizaciones y quieres productificarlas o escalarlas | Un par que revisa tu diseño, te pide el número que falta y te dice qué parte es teatro. Evals, cuatro paradas, gobernanza y paquete de ejecución para que otro lo corra. |
| Empiezas, pero ya sabes bastante | Del proceso al diseño con `/arrancar`: qué va en un `if`, qué va en IA y qué va a un humano. Patrones que corren, hechos fechados y un agente que no te explica lo que ya sabes. |

No es un chatbot de curso ni un tutorial de Claude Code: es infraestructura que te sirve para la automatización #1 y para la #12.

## Empieza en 3 pasos

1. **Instala Claude Code** con el instalador nativo. Detalle, Windows y alternativa con npm en [docs/instalacion.md](docs/instalacion.md).

   ```bash
   curl -fsSL https://claude.ai/install.sh | bash
   claude --version
   ```

2. **Crea tu copia** en [github.com/nabolom/agentic-ai-automation-mentor-agent-2026](https://github.com/nabolom/agentic-ai-automation-mentor-agent-2026) con **Use this template**, márcala como **Private**, clónala y entra con `claude`.

3. **Corre `/rumbo`** y después **`/arrancar`**.

¿Ya tienes tu repo del curso creado desde ai-automation-expert? Trae el assessment con dos `curl`: [docs/antes-de-s2.md](docs/antes-de-s2.md).

## Empieza aquí como alumno

Si quieres una guía de 15 minutos, sigue [`ALUMNO-EMPIEZA-AQUI.md`](ALUMNO-EMPIEZA-AQUI.md). Incluye la ruta Claude Code/Cowork, el fallback sin credenciales y el criterio de salida del núcleo.

Si eres facilitador, usa el [`Kit del facilitador`](facilitador/README.md). Para comprobar que la copia está sana antes de clase, ejecuta:

```bash
PYTHONDONTWRITEBYTECODE=1 python3 verificar.py
```

El mapa visual de la experiencia está en [`docs/visuales/mapa-del-curso.mmd`](docs/visuales/mapa-del-curso.mmd) y en [`PNG`](docs/visuales/mapa-del-curso.png).

## Tu ruta

`/rumbo` asigna una de cinco rutas. Sale de lo que quieres y de lo que tienes; la evidencia decide cómo se te acompaña, no la ruta.

| Ruta | Te toca si | Foco: qué llevas a S2 |
|---|---|---|
| `construir` | Tu estado actual es `nada` o `prototipo` | 6 casos núcleo recordados, no inventados, de tu proceso, con la salida esperada de cada uno; 10 para la suite extendida |
| `endurecer` | Corre para ti y el usuario final eres tú | El export o prompt actual y 6 casos reales; completa a 10 si el tiempo lo permite |
| `productificar` | Corre para ti y el usuario final es tu equipo, internos o clientes | El export y el nombre de quien lo va a correr sin ti |
| `escalar` | Ya corre para otros | El costo real de un mes (consola o factura) y 6 casos de producción; 10 para la suite extendida |
| `todavia-no` | No describes un artefacto observable, o no tienes número ni forma de medirlo | El mapa del proceso con hechos, inferencias y faltantes separados |

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

## Qué hay en este repo

```
CLAUDE.md             el cerebro
ACOMPANAMIENTO.md     cómo te acompaña según lo que demostraste en /rumbo
LICENSE               MIT
rumbo.md              tu assessment (lo genera /rumbo)
.claude/commands/     los comandos de arriba
.claude/skills/       capacidades — se cargan bajo demanda
.claude/settings.json permisos: el agente no lee .env ni secretos
docs/                 guías para personas: instalación, antes de S2, doctrina, competencias, seguridad
facilitador/          checklist, guiones S2–S4, rescates y debrief
patrones/             los siete patrones, con estructura y trampas
referencias/          hechos verificados y FECHADOS ← lo más valioso
proyectos/            tus automatizaciones
curso/                las guías de cada sesión
verificar.py          una verificación local de pruebas, fixtures, tasas y enlaces
.github/workflows/    validación automática en cada push y pull request
```

## Cómo te acompaña

El nivel de evidencia que demostraste en `/rumbo` decide el modo en cada tema. Detalle en [ACOMPANAMIENTO.md](ACOMPANAMIENTO.md).

| Nivel | Modo | Qué hace |
|---|---|---|
| 0–1 | Enseñar | Explica el mecanismo en corto, con un ejemplo, y hace una sola pregunta |
| 2 | Retar | No explica: pide la evidencia que falta (el número, el archivo, el criterio) |
| 3 | Revisar como par | No guía: señala riesgos y contradicciones; tú conduces |

## Doctrina

Los cinco principios que más pesan. Los catorce, en [docs/doctrina.md](docs/doctrina.md); la versión completa, en [CLAUDE.md](CLAUDE.md).

- **Si puedes escribirlo como un `if`, que sea un `if`.**
- **Diseña la falla, no el éxito.**
- **Salida estructurada o no hay sistema.**
- **El harness importa más que el modelo.**
- **La condición de parada debe ser verificable sin el modelo.**

## Hechos y fechas

Los archivos de `referencias/` están verificados al **9 de octubre de 2026** (Claude API, MCP, n8n, OKF, METR, multiagente; LangChain, harness y gobernanza al 13 de julio de 2026).
Se pudren: corre `/verificar` cada dos meses, o antes de cualquier decisión de costos que importe.
Al armar este repo, tres de los blogs mejor rankeados de "Claude API pricing 2026" tenían datos viejos o mal, incluyendo el primer resultado de Google. **Siempre la fuente oficial.**

## Créditos y licencia

[MIT](LICENSE) © 2026 León Ruiz. Curso Productividad con Claude (IA) AVANZADO, [Collective Academy](https://collectiveacademy.com/). Basado en [ai-automation-expert](https://github.com/nabolom/ai-automation-expert) (Q3 2026).
