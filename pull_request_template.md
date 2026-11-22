## Qué cambia

<!-- Una o dos líneas. Obligatorio: si eres contribuidor calificado, esto y «Cómo se probó» te permiten hacer merge de tu propio PR. -->

Closes #

## Cómo se probó

<!-- Comandos, entorno de PlatformIO, banco, simulación. Pega la salida relevante. -->

## Checklist

- [ ] Commits `<área>: <qué>`, en español y firmados (`git commit -s`)
- [ ] CI en verde
- [ ] La lógica nueva trae su prueba (o explico arriba por qué no aplica)
- [ ] Docs actualizados (README, `docs/`, ADR si cruza áreas)
- [ ] Sin secretos ni binarios pesados

## Safety-critical

<!-- Marca solo si el PR toca driver, protocolo, lazo de control o navegación del ADC, frenos/dirección o paro de emergencia. Si no, borra esta sección. -->

- [ ] Etiqueta `safety-critical` puesta
- [ ] Sesión de prueba de banco enlazada (`sys-integration/tests/AAAA-MM-DD-tema.md`) o issue de prueba posterior (`test-pending`)
- [ ] Reglas de banco respetadas (sin potencia al grabar firmware que activa el PWM; pruebas sin motor solo con USB)
- [ ] Plan de reversión: release o rama a la que se vuelve si falla
