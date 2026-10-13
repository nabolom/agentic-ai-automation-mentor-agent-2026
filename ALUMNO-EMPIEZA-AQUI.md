# Empieza aquí — Aprendedor(a)

Esta página es tu **primer recorrido**. No necesitas leer todo el repositorio antes de empezar.

## Tu objetivo

En las sesiones vas a convertir una automatización o una idea en un sistema que puedas explicar, medir y dejar operable por otra persona.

La secuencia es:

```text
proceso → decisión → evals → diagnóstico → límites → handoff
```

## Primeros 15 minutos

### 1. Abre tu copia

Usa la plantilla de GitHub para crear tu copia privada del repositorio. Después entra a la carpeta con Claude Code.

Si ya tienes una copia del curso, trabaja en ella; no necesitas crear otra.

### 2. Haz el preflight

Comprueba lo mínimo:

```bash
claude --version
git --version
claude doctor
```

No pegues API keys en archivos ni en mensajes. Las credenciales, si algún día hacen falta, viven fuera del repositorio.

Si tu siguiente actividad es S2, sigue la [Ruta crítica antes de S2](docs/ruta-critica-antes-de-s2.md): camino dorado, `/rumbo`, una decisión y seis casos.

Si trabajas en **Cowork**, abre la misma carpeta y sigue esta guía; la interfaz cambia, pero el contrato, los casos y la evidencia son los mismos. Cuando una actividad pida un comando de terminal, ejecútalo en la terminal disponible o usa el fallback offline/papel.

### 3. Elige tu ruta de trabajo

| Si… | Empieza por… |
|---|---|
| Ya tienes una automatización o un proceso propio | `curso/00-ruta-de-la-cohorte.md` y `/rumbo` |
| Tienes una idea, pero todavía no un proceso acotado | `/rumbo` y después `/arrancar` |
| Claude Code o la autenticación no funcionan | `ejemplo/README.md` y el camino dorado offline |
| Trabajas en n8n, Make, CoWork u otra herramienta visual | La ruta visual de la sesión correspondiente; el contrato es el mismo |

### 4. Corre el camino dorado

Si quieres un suelo común o tu entorno no está listo, usa el ejemplo:

```bash
python3 ejemplo/camino_dorado.py --modo offline --version v1
```

Si no tienes Python, abre `ejemplo/casos.json` y recorre los seis casos núcleo en papel. El aprendizaje es el mismo:

```text
if → IA → salida estructurada → validación → humano
```

### 5. Entra a Claude Code

Dile:

```text
Lee CLAUDE.md, ACOMPANAMIENTO.md y curso/00-ruta-de-la-cohorte.md.
Ayúdame a trabajar una sola decisión de una automatización.
Si todavía no tengo un proceso acotado, llévame primero por el camino dorado.
No inventes mis salidas esperadas: ayúdame a fijarlas.
```

## Qué debes traer a la siguiente sesión

Para el núcleo de la cohorte:

- un proceso o el camino dorado;
- una sola decisión de IA;
- seis casos: 4 típicos, 1 límite y 1 adversarial;
- la salida esperada de cada caso;
- cualquier export, prompt o nota que ya tengas.

Los diez casos son una **extensión**, no un requisito para avanzar.

## Qué no necesitas hacer todavía

- No necesitas construir un agente autónomo.
- No necesitas conectar una API real.
- No necesitas usar n8n si tu proceso vive en otra herramienta.
- No necesitas construir un loop.
- No necesitas leer todas las referencias.
- No necesitas traer datos sensibles reales: usa datos sintéticos o anonimizados.

## Cómo sabrás que avanzaste

Al terminar el núcleo deberás poder responder:

1. ¿Qué parte es un `if`?
2. ¿Qué parte necesita IA y por qué?
3. ¿Cuánto acierta sobre tus seis casos?
4. ¿Cómo sabes que funcionó sin preguntarle al modelo?
5. ¿Qué acción nunca dejarías automática?
6. Si tú desapareces mañana, ¿quién lo corre?

## Punto de entrada completo

Después de estos 15 minutos, sigue la [Ruta de la cohorte](curso/00-ruta-de-la-cohorte.md). El resto del repositorio es referencia bajo demanda; no es una lista de lectura obligatoria.
