# S2 — Guion del facilitador

**Objetivo:** que cada alumno salga con un caso acotado, una decisión de IA y una primera medición.

**Guía técnica:** [`curso/S2-evals.md`](../curso/S2-evals.md)
**Ruta:** [`curso/00-ruta-de-la-cohorte.md`](../curso/00-ruta-de-la-cohorte.md)
**Ejemplo:** [`ejemplo/README.md`](../ejemplo/README.md)

## Agenda de 150 minutos

| Minutos | Tú haces | El alumno produce | Pregunta de transición |
|---:|---|---|---|
| 0–15 | Recuperas `if`, IA, herramienta y humano | Una decisión explicada | “¿Por qué esto no es solo un prompt?” |
| 15–35 | Corres/enseñas el camino dorado, incluido un caso que escala | Lectura del recorrido | “¿Dónde no debe decidir el modelo?” |
| 35–55 | Ayudas a elegir proceso propio o caso común | Un solo proceso | “¿Qué queda fuera hoy?” |
| 55–80 | Pides mapear flujo y definición de terminado | `flujo.md` y `alcance.md` | “¿Cómo lo verificaría otra persona?” |
| 80–100 | Ayudas a diseñar una decisión de IA | Contrato de salida | “¿Qué parte podría ser un `if`?” |
| 100–120 | Pides fijar seis casos | Evals 4/1/1 | “¿Cuál es el caso que más te preocupa?” |
| 120–140 | Corres la línea base | Tasa + salida cruda | “¿Qué falló exactamente?” |
| 140–150 | Cierras con diagnóstico corto | Causa probable + exit ticket | “¿Qué vas a cambiar y qué no?” |

## Frases útiles

- “No necesito que me digas que funciona; necesito que me enseñes cómo lo sabes.”
- “La salida esperada la fija la persona que conoce la operación; el agente no la inventa.”
- “Seis casos reales hoy valen más que diez inventados.”
- “Primero medimos el sistema como está. Después decidimos qué tocar.”

## Señales de atasco

| Señal | Intervención |
|---|---|
| Está describiendo un agente que hace todo | Pide una sola decisión y cuatro categorías: `if`, IA, herramienta, humano |
| No tiene proceso propio | Devuélvelo al camino dorado; la transferencia puede quedar para después |
| Quiere escribir el prompt antes de los casos | Pide primero cuatro típicos, un límite y un adversarial |
| No puede definir salida esperada | Reduce la decisión a un campo verificable |
| Está instalando durante la clase | Mueve al fallback offline/papel y conserva el objetivo |
| Quiere completar diez casos antes de medir | Recuérdale que seis es el núcleo válido |

## Cierre mínimo

El alumno debe poder mostrar:

- una decisión de IA acotada;
- seis casos con salida esperada;
- una tasa de línea base;
- la salida cruda de un fallo;
- una causa probable, sin culpar automáticamente al modelo.

Si no llega al proyecto propio, el camino dorado sigue siendo un cierre válido para la sesión; documenta la transferencia como siguiente paso.
