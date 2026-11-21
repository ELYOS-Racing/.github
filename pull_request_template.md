## Qué cambia

<!-- Una o dos líneas. -->

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

<!-- Marca solo si el PR toca driver, protocolo, frenos/dirección del ADC o paro de emergencia. Si no, borra esta sección. -->

- [ ] Etiqueta `safety-critical` puesta
- [ ] Sesión de prueba de banco enlazada (`sys-integration/tests/AAAA-MM-DD-tema.md`)
- [ ] Reglas de banco respetadas (sin potencia al grabar firmware que activa el PWM; pruebas sin motor solo con USB)
- [ ] Plan de reversión: release o rama a la que se vuelve si falla
- [ ] 2 aprobaciones
