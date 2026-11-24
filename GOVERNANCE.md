# Gobernanza de Elyos Racing Team

Reglas de la organización [`ELYOS-Racing`](https://github.com/ELYOS-Racing). Aplican a todos los repos. Cambiarlas requiere un PR a este archivo aprobado por **2 owners** (regla 10).

## 1. Roles

| Rol | Quién | Qué puede hacer |
|---|---|---|
| Owner | El profesor asesor (permanente) y de 1 a 4 líderes | Administra la org: repos nuevos, gastos, servicios con costo y desempates. Puede usar el override de la regla 4 |
| Líder de área | Uno por área (tabla de la regla 4) | Decide dentro de su área, aprueba y mergea en los repos de su área, declara calificados y mantiene el Project del área |
| Contribuidor calificado | Quien el líder declare para un repo (tabla de la regla 4) | Mergea su propio PR en ese repo y aprueba los PR de otros en él |
| Contribuidor | Integrante del team de su área | Escribe en los repos de su área, siempre por PR |
| Alumni / externo | Team `alumni`, outside collaborators | Solo lectura en repos puntuales |

Los profesores asesoran: se les informa, pero no aprueban código.

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

### Cómo entra un cambio

- **Todo entra por PR, con el CI en verde.** Nadie empuja directo a `main`.
- **Cada PR lo aprueba otra persona:** un code owner de los archivos que toca. Nadie aprueba su propio PR.
- **Mergear el propio PR sin esperar aprobación** solo lo pueden hacer el líder, en los repos de su área, y el contribuidor calificado, en el repo para el que lo declararon. En los dos casos, la descripción del PR dice **qué cambia y cómo se probó**.
- **`safety-critical`** (driver, protocolo, lazo de control y navegación del ADC, frenos, dirección y paro de emergencia): además, el PR enlaza una **sesión de banco** o un **issue de prueba posterior** (`type:test`, etiqueta `test-pending`), que se cierra con su sesión antes del siguiente gate o release.
- Las ramas se borran al hacer merge.

### Líderes y calificados

| Área | Repos | Líder |
|---|---|---|
| Control | `fw-motor-driver`, `fw-protocol` | `luisxavierxd` (desde 21-nov-2026) |
| ADC | `adc-stack`, `fw-protocol` | `luisxavierxd` (desde 21-nov-2026) |
| Telemetría | `fw-telemetry`, `sw-dashboard`, `sw-strategy`, `fw-protocol` | Por nombrar; interino: `luisxavierxd` |
| Electrónica | `hw-electronics` | Por nombrar |
| Mecánica | `mech-cad` | Por nombrar |

`fw-protocol` es el contrato entre placas, así que pertenece a tres áreas y lo lideran sus tres líderes.

En **electrónica y mecánica**, el líder en GitHub no es necesariamente el líder técnico del área:

- El **líder técnico** decide el diseño (qué placa, qué pieza), aunque no trabaje en GitHub.
- El **líder de GitHub** es quien digitaliza: KiCad, BOM, numeración de piezas y releases. Es quien va en `electronics-leads` o `mechanical-leads`, aprueba los PR y mergea. Revisa que lo digitalizado cumpla las reglas del repo (DRC, BOM, numeración).
- Cuando un PR cambia el diseño, el issue o el PR registra la aprobación del líder técnico (por ejemplo: «aprobado por <líder técnico> en la reunión del 3-dic»).

Los contribuidores calificados se declaran **por repo**: que alguien sea confiable en la web no lo hace confiable en el firmware de la misma área. Se agregan por PR a esta tabla, aprobado por el líder del área.

| Repo | Contribuidores calificados | Desde |
|---|---|---|
| — | Ninguno todavía | — |

Que pocas personas concentren el conocimiento es un riesgo registrado en `sys-integration` (bus factor). Se mitiga formando gente, no agregando aprobaciones.

### Override de owners

Los owners pueden mergear sin las aprobaciones requeridas en cambios de **estructura, migración o mantenimiento de la org**: plantillas, licencias, CI, configuración, renombres y documentación de organización. **Nunca** en lógica `safety-critical`. El PR dice que se usó el override y por qué.

### Cómo se aplica en GitHub (plan Team)

| Quién | Team | Permiso | Se salta la revisión en |
|---|---|---|---|
| Líder de área | `leads` y `<area>-leads` | Write en todos los repos; Maintain en los de su área | Los repos de su área |
| Contribuidor calificado | `<repo>-qualified` (se crea con el primer calificado del repo) | El de su team de área | Ese repo |
| Contribuidor | Su team de área (`fw`, `hw`, `mech`, `adc`, `ops`) | Write en los repos de su área | — |
| Owner | — | Admin | Todos (es el override) |
| Cuenta de automatización | `merge-bypass` | — | Todos |

- Saltarse la revisión solo funciona dentro de un PR, y el CI (`ci-ok`) no se lo salta nadie.
- Los profesores no están en ningún team que se salte la revisión.
- Detalle y script en [`sys-integration/docs/MIGRACION_GITHUB_TEAM.md`](https://github.com/ELYOS-Racing/sys-integration/blob/main/docs/MIGRACION_GITHUB_TEAM.md).

Idioma: regla 11. Detalle del flujo en [`CONTRIBUTING.md`](CONTRIBUTING.md).

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
- El DCO (`git commit -s`) certifica el derecho a aportar el código. Todo commit que entra por PR lo lleva, con el correo de su autor.
- **Autores y coautores de un commit** (`Co-authored-by`) solo pueden ser personas que firman el DCO en ese mismo PR. Quien no es de la org y quiere aportar entra como colaborador externo y hace sus propios commits firmados; no se le acredita en los commits de otro.
- **Las herramientas de IA no se acreditan como coautoras.** Se pueden usar; quien firma el commit responde por el código como si lo hubiera escrito.
- El check `autoria` (en `ci-ok` de cada repo) revisa las tres cosas en cada PR.
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
