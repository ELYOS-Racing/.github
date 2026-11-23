# Gobernanza de Elyos Racing Team

Reglas de la organización [`ELYOS-Racing`](https://github.com/ELYOS-Racing). Aplican a todos los repos. Cambiarlas requiere un PR a este archivo aprobado por **2 owners** (regla 10).

## 1. Roles

| Rol | Quién | Qué puede hacer |
|---|---|---|
| Owner | Profesor asesor (permanente) y 1–4 líderes | Administra la org; aprueba repos nuevos, gastos y servicios con costo; desempata; override en cambios de estructura (regla 4). Los profesores son asesores, no aprobadores técnicos |
| Líder de área | Uno por área: Write en todos los repos (team `leads`) y Maintain en los de su área (team `<area>-leads`) | Decide dentro de su área; es contribuidor calificado; declara a otros calificados; mantiene su Project |
| Contribuidor calificado | El líder de cada área (en todos sus repos), más quien él declare para un repo en la tabla de la regla 4 | Puede hacer merge de su propio PR con CI en verde y descripción de qué cambia y cómo se probó; aprueba los PRs de los contribuidores de su área |
| Contribuidor | Integrante del team de su área | Escribe en los repos de su team, siempre por PR; su PR lo aprueba un contribuidor calificado del área |
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

- **Todo entra por PR** (nada de push directo a `main`) y con **CI en verde**.
- **Contribuidor calificado.** Cada área (control, ADC, telemetría, electrónica, mecánica) tiene contribuidores calificados: el líder del área lo es siempre y puede declarar a otros. Un calificado **puede hacer merge de su propio PR** si la descripción dice **qué cambia y cómo se probó**.
- **Quien no es calificado** necesita la aprobación de un calificado de su área. Así se forma a la gente nueva.
- **`safety-critical`** (driver, protocolo, lazo de control y navegación del ADC, frenos/dirección, paro de emergencia): además, **sesión de banco enlazada** o un **issue de prueba posterior** (`type:test`, etiqueta `test-pending`) enlazado al PR, que se cierra con su sesión antes del siguiente gate o release.
- Los profesores son asesores: se les informa, no son aprobadores técnicos.

  | Área | Repos | Líder |
  |---|---|---|
  | Control | `fw-motor-driver`, `fw-protocol` | `luisxavierxd` (desde 21-nov-2026) |
  | ADC | `adc-stack`, `fw-protocol` | `luisxavierxd` (desde 21-nov-2026) |
  | Telemetría | `fw-telemetry`, `sw-dashboard`, `sw-strategy`, `fw-protocol` | Por nombrar; interino: `luisxavierxd` |
  | Electrónica | `hw-electronics` | Por nombrar |
  | Mecánica | `mech-cad` | Por nombrar |

  `fw-protocol` es el contrato entre placas: es de control, ADC y telemetría, y lo lideran los tres.

  **Calificados por repo** (además de los líderes de su área):

  | Repo | Contribuidores calificados | Desde |
  |---|---|---|
  | — | Ninguno todavía | — |

  Un calificado se declara **por repo**, por PR a esta tabla, aprobado por el líder del área: ser confiable en un repo no lo hace confiable en los demás de su área. Con GitHub Team, el bypass de los rulesets de revisión (siempre solo en PR y nunca sobre el CI) va así: cada **líder**, en el team `<area>-leads`, en todos los repos de su área; cada **calificado**, en el team `<repo>-qualified`, solo en ese repo (el team se crea con el primer calificado). En todos los repos, solo los owners (override, más abajo) y el team `merge-bypass`, que es para cuentas de automatización. Los profesores no van en ninguno. Detalle en [`sys-integration/docs/MIGRACION_GITHUB_TEAM.md`](https://github.com/ELYOS-Racing/sys-integration/blob/main/docs/MIGRACION_GITHUB_TEAM.md). La concentración de conocimiento en pocas personas es un riesgo registrado en `sys-integration` (bus factor): se mitiga formando gente, no con más aprobaciones.
- Las ramas se borran al hacer merge.
- **Override de owners.** Los owners pueden hacer merge con bypass de reglas (sin las aprobaciones requeridas) en cambios de **estructura, migración o mantenimiento de la org**: plantillas, licencias, CI, configuración, renombres y documentación de organización. Nunca en cambios de lógica `safety-critical`. El PR dice que se usó el override y por qué. Con GitHub Team se implementa como bypass de los owners (`OrganizationAdmin`) en los rulesets de revisión, solo en PR y nunca sobre el CI.
- Idioma: regla 11.
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
- Titulares: Luis Xavier García Pimentel Ascencio y Elyos Racing Team (ver el `Required Notice` de cada `LICENSE.md`).

## 9. Secretos

- Nunca en el código. Se guardan como secretos de la org.
- `gitleaks` en pre-commit y en CI.
- Secreto filtrado = rotarlo y avisar a los owners (ver [`SECURITY.md`](SECURITY.md)).

## 10. Cambios a esta gobernanza

PR a `.github/GOVERNANCE.md` con la aprobación de 2 owners.

## 11. Idioma: un idioma por artefacto, según quién lo lee

- **Español** (lo lee el equipo): README, `docs/`, onboarding, ADRs, sesiones de prueba, traspasos, issues, PRs, commits, plantillas y comentarios en el código. El `CHANGELOG.md` interno también.
- **Inglés** (lo lee alguien de fuera): perfil público de la org (`.github/profile/README.md`), notas de release, manifiestos de competencia y documentos que salen del equipo (reportes técnicos para Shell, propuestas a patrocinadores, postulaciones a premios). También el README y el «About» de cualquier repo público.
- **Inglés siempre:** identificadores, nombres de repos, ramas, etiquetas y tags.
- No se traduce la documentación interna (dos versiones = una desactualizada). Notas de release: borrador en inglés generado desde los PRs mergeados, revisado por una persona antes de publicar.
- ICDs en español, con los nombres de señales, mensajes y unidades exactamente como en el código.
- Si un repo se vuelve público, se le agrega un README en inglés en ese momento.

## 12. Dependencias ADC ↔ prototipo en un solo sentido

Los issues de `adc-stack` pueden estar bloqueados por issues del prototipo (por ejemplo, de `fw-protocol`). **Ningún issue del prototipo puede depender del ADC**: el autónomo nunca retrasa al coche de competencia.
