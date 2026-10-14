# Empieza aquí — Aprendedor(a)

Esta página te lleva a tu **primera sesión técnica**. La reunión anterior fue de bienvenida y contexto; no necesitas asumir que ya sabes construir un agente.

## Tu objetivo de hoy

Vas a entrar al repositorio con Claude Code y el Agente Mentor para convertir una idea, un proceso o una automatización existente en **una decisión concreta que podamos observar y medir**.

```text
proceso → decisión → casos → medición → diagnóstico → límites → handoff
```

No necesitas construir un agente completo. Según lo que traigas, puedes descubrir, construir, endurecer o productificar/escalar.

## Antes de abrir Claude Code

1. Usa **Use this template** para crear tu copia privada o abre la copia que ya tienes.
2. Abre una terminal en la carpeta de tu repositorio.
3. Verifica que Claude Code exista:

```bash
claude --version
```

4. Entra al repositorio:

```bash
claude
```

Si algo falla, guarda el mensaje o una captura. No conviertas tu primera sesión en una batalla de instalación: usa el [Camino dorado](ejemplo/README.md) offline o en papel y lleva el bloqueo a office hours.

## Primer mensaje al Agente Mentor

Pega esto dentro de Claude Code:

```text
Lee CLAUDE.md y ACOMPANAMIENTO.md.
Dime qué repositorio abrí, qué hace el Agente Mentor y qué comandos del proyecto están disponibles.
No edites archivos todavía.
```

Después continúa con:

```text
Hazme una pregunta a la vez.
Ayúdame a elegir entre descubrir, construir, endurecer o productificar/escalar.
No inventes mi proceso, mis casos ni mis salidas esperadas.
Si todavía no tengo un proceso acotado, usa el camino dorado como andamio.
```

## Elige tu track

| Si… | Tu track | Tu salida de hoy |
|---|---|---|
| Tienes una idea o proceso, pero nada construido | **Descubrir** | Proceso acotado y decisión que vale la pena explorar |
| Tienes un prototipo o automatización que solo tú corres | **Construir** | Mapa `if` / IA / herramienta / humano y una decisión |
| Ya funciona, pero falla o no tiene número | **Endurecer** | Una falla, una decisión difícil y una línea base posible |
| Ya corre para otras personas | **Productificar / escalar** | Cuello de botella, riesgo, costo o handoff que falta |

Después, si aplica, ejecuta `/rumbo`. El assessment fija una ruta; el acompañamiento te ayuda a trabajarla sin inventar evidencia.

## El caso común

Abre [`ejemplo/README.md`](ejemplo/README.md) y lee **Problema**, **Qué vas a hacer aquí** y **La secuencia que enseña**.

Si no tienes proyecto propio, el camino dorado es tu andamio válido. Si ya tienes automatización, úsalo para calibrar el criterio y luego transfiérelo a una sola decisión de tu sistema.

```text
if → IA → salida estructurada → validación → humano
```

## Entregable mínimo de la sesión

Guarda en una nota, en `rumbo.md` o en el archivo que el Mentor te indique:

- una frase de proceso o caso;
- una sola decisión de IA;
- tres casos ancla: uno típico, uno límite y uno adversarial;
- la salida esperada de cada caso;
- una duda concreta o siguiente paso.

Después de la sesión completa la suite de seis casos: 4 típicos, 1 límite y 1 adversarial. Los diez casos son opcionales.

## Qué no necesitas hacer hoy

- No necesitas construir un agente autónomo.
- No necesitas conectar una API real.
- No necesitas instalar Node/NPM si tu ruta no los usa.
- No necesitas exigir que tu automatización existente se vuelva un agente.
- No necesitas completar diez casos.
- No necesitas pegar datos sensibles en el repo o en el chat.

## Si algo falla

- **Claude Code no inicia:** conserva el error y usa el camino dorado.
- **Git no está listo:** trabaja con la copia disponible, Cowork, ZIP o papel; instala después.
- **No tienes Python:** abre `ejemplo/casos.json` y recorre los casos manualmente.
- **Tu automatización ya existe:** no vuelvas a empezar; elige una falla o cuello de botella.
- **No tienes proceso propio:** usa el caso común y marca la transferencia como siguiente paso.

## Cómo sabrás que avanzaste

Puedes responder:

1. ¿Qué parte es un `if`?
2. ¿Qué parte necesita IA y por qué?
3. ¿Qué salida esperas?
4. ¿Qué caso podría romper la decisión?
5. ¿Qué acción nunca dejarías automática?
6. ¿Qué vas a medir después?

## Referencias

- [Sesión S1+S2 — Panorama y primera medición](curso/S1-S2-panorama-y-evals.md)
- [Ruta de la cohorte](curso/00-ruta-de-la-cohorte.md)
- [Camino dorado](ejemplo/README.md)
- [Dependencias y preflight](docs/dependencias-y-preflight.md)
- [Guía de instalación](docs/instalacion.md)
