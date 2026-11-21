# Seguridad

## Reportar un problema

**No abras un issue público.** Usa *Report a vulnerability* (pestaña Security del repo) o escribe directamente a un owner de la org.

Incluye qué encontraste, dónde (repo, archivo, commit) y cómo reproducirlo.

## Secretos filtrados

Si un secreto (token, contraseña, llave, credencial de un servicio) llega a un commit, aunque sea en una rama:

1. **Rótalo de inmediato** en el servicio que lo emitió. Borrar el commit no basta: el historial y los forks lo conservan.
2. **Avisa a los owners** con qué secreto era y desde cuándo estuvo expuesto.
3. Registra el incidente en el inventario de secretos del equipo.

## Prevención

- Los secretos viven como secretos de la org o del repo, nunca en el código.
- `gitleaks` corre en pre-commit y en CI.
- Antes de hacer público o transferir un repo, se corre `gitleaks detect` sobre todo su historial.

## Seguridad física

El firmware del driver maneja un inversor de 48 V / 45 A. Las reglas de banco (alimentación solo USB en pruebas sin motor, confirmar que no hay potencia antes de grabar firmware que active el PWM, etc.) están en `docs/DECISIONES.md` de `fw-motor-driver`. Un PR `safety-critical` sin evidencia de banco no se aprueba.
