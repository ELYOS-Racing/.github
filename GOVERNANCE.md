# Gobernanza de Silca Elyos Racing

Reglas de la organización [`ELYOS-Racing`](https://github.com/ELYOS-Racing). Aplican a todos los repos. Cambiarlas requiere un PR a este archivo aprobado por **2 owners** (regla 10).

## 1. Roles

| Rol | Quién | Qué puede hacer |
|---|---|---|
| Owner | Profesor asesor (permanente) y 1–2 líderes | Administra la org; aprueba repos nuevos, gastos y servicios con costo; desempata |
| Líder de área | Un maintainer por área (team `leads`) | Decide dentro de su área; revisa y aprueba PRs; mantiene su Project |
| Contribuidor | Integrante del team de su área | Escribe en los repos de su team, siempre por PR |
| Alumni / externo | Team `alumni`, outside collaborators | Solo lectura en repos puntuales |

## 2. Decisiones

- **Dentro de un área:** decide su líder.
- **Entre áreas** (protocolo, interfaces, arquitectura, sensores): PR de un ADR en `sys-integration/docs/adr/`, aprobado por los líderes afectados.
- **Lo que toca el coche físico o tiene costo:** lo aprueban los owners.

## 3. Acceso

- Por team, nunca individual. Altas por issue en `ops-tasks`.
- 2FA obligatoria (la org la exige).
- Permiso base de la org: Read. Escritura solo por team.
- Al cierre de cada semestre, quien sale pasa a `alumni` y se revisan los accesos.

## 4. Contribuciones

- Todo entra por PR; nadie aprueba el suyo.
- **1 aprobación + CI en verde** para hacer merge.
- **`safety-critical`** (driver, protocolo, frenos/dirección del ADC, paro de emergencia): **2 aprobaciones + evidencia de banco** (sesión de prueba enlazada).
- Las ramas se borran al hacer merge.
- Docs en español; identificadores de código en inglés.
- Detalle del flujo en [`CONTRIBUTING.md`](CONTRIBUTING.md).

## 5. Repos

- Un repo nuevo requiere aprobación de un owner, seguir la convención de nombre (`<dominio>-<componente>`, kebab-case, en inglés, sin "elyos", sin años ni personas) y nacer con `README`, `LICENSE` y `CODEOWNERS`.
- Los repos **nunca se borran**: se archivan.

## 6. Releases

- Solo desde CI; los tags son inmutables.
- Cada release de sistema tiene su manifiesto en `sys-integration/releases/`.
- El código de cada release de competencia entra además a `legacy/<año>/` de su repo.

## 7. Traspaso semestral

- Checklist (issue template de traspaso) + reporte en `sys-integration/handover/AAAA-S-usuario.md`.
- Quien entra reproduce el último release validado antes de tocar `main`.

## 8. Propiedad intelectual

- Las contribuciones quedan bajo la licencia del repo (PolyForm Strict 1.0.0 salvo excepciones documentadas en su `NOTICE.md`).
- El DCO (`git commit -s`) certifica el derecho a aportar el código.
- Titular por confirmar con la Oficina de Transferencia de Tecnología del Tec.

## 9. Secretos

- Nunca en el código. Se guardan como secretos de la org.
- `gitleaks` en pre-commit y en CI.
- Secreto filtrado = rotarlo y avisar a los owners (ver [`SECURITY.md`](SECURITY.md)).

## 10. Cambios a esta gobernanza

PR a `.github/GOVERNANCE.md` con la aprobación de 2 owners.

## 11. Dependencias ADC ↔ prototipo en un solo sentido

Los issues de `adc-stack` pueden estar bloqueados por issues del prototipo (por ejemplo, de `fw-protocol`). **Ningún issue del prototipo puede depender del ADC**: el autónomo nunca retrasa al coche de competencia.
