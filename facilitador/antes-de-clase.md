# Antes de clase — checklist del facilitador

## Un día antes

- [ ] Compartí la copia correcta del repositorio o la plantilla de GitHub.
- [ ] Compartí [`ALUMNO-EMPIEZA-AQUI.md`](../ALUMNO-EMPIEZA-AQUI.md).
- [ ] Pedí completar `claude --version`, `git --version` y `claude doctor`.
- [ ] Recordé que no se pegan API keys en el repo ni en mensajes.
- [ ] Confirmé que el grupo sabe dónde encontrar la [Ruta de la cohorte](../curso/00-ruta-de-la-cohorte.md).
- [ ] Preparé el camino dorado offline como fallback.
- [ ] Preparé el caso común en pantalla o compartido en el repositorio.

## Antes de abrir la sesión

- [ ] El repositorio abre desde la rama o copia que usarás en clase.
- [ ] El camino dorado offline corre sin credenciales.
- [ ] La prueba reproducible está disponible en `ejemplo/test_camino_dorado.py`.
- [ ] La terminal y Claude Code están visibles para la demo.
- [ ] Tienes a mano la tabla de tiempos de la sesión.
- [ ] Tienes un plan B si falla Claude Code, Python, la herramienta visual o la autenticación.

## Qué debe estar visible

1. La secuencia:

   ```text
   if → IA → salida estructurada → validación → humano
   ```

2. El núcleo:

   ```text
   6 casos = 4 típicos + 1 límite + 1 adversarial
   ```

3. La pregunta de transferencia:

   > ¿Qué proceso propio se parece a este caso?

## Durante la sesión

- [ ] Cada bloque termina con un checkpoint observable.
- [ ] Nadie trabaja dos procesos a la vez.
- [ ] Las salidas esperadas quedan fijadas por el Aprendedor(a).
- [ ] Los Aprendedores(as) distinguen ruta visual y ruta código/API sin cambiar el criterio.
- [ ] Un fallo se analiza antes de cambiar el prompt.
- [ ] Los avanzados trabajan la extensión sin convertirla en requisito para el grupo.

## Si el grupo se retrasa

1. Vuelve al camino dorado.
2. Reduce el proyecto a una sola decisión.
3. Trabaja con seis casos núcleo.
4. Cambia live por offline o por papel.
5. Deja loop, MCP, costos y multiagente como extensión.

## Si el grupo termina antes

Ofrece solo una extensión:

- completar la suite de 10 casos;
- medir costo o confianza;
- correr una comparación end-to-end;
- justificar por qué sí o no necesita loop;
- preparar un handoff más operable;
- revisar S5/multiagente como decisión arquitectónica.
