# .github

Archivos comunes de la organización [`ELYOS-Racing`](https://github.com/ELYOS-Racing). **Repo público**: solo contiene plantillas y reglas, nunca código ni secretos.

| Archivo | Qué es |
|---|---|
| [`profile/README.md`](profile/README.md) | Página pública de la org |
| [`GOVERNANCE.md`](GOVERNANCE.md) | Roles, decisiones, acceso, contribuciones, releases, traspasos |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | Flujo issue → rama → PR, commits, etiquetas |
| [`SECURITY.md`](SECURITY.md) | Reportar vulnerabilidades y secretos filtrados |
| [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) | Contributor Covenant 2.1 |
| [`pull_request_template.md`](pull_request_template.md) | Plantilla de PR con checklist `safety-critical` |
| [`ISSUE_TEMPLATE/`](ISSUE_TEMPLATE/) | Formularios de tarea, bug, riesgo y solicitud de cambio (PMBOK 8); tarea y bug con desplegable de área |
| [`.github/workflows/area-label.yml`](.github/workflows/area-label.yml) | Workflow reutilizable que etiqueta `area:*` y `safety-critical` desde los formularios |
| [`workflow-templates/`](workflow-templates/) | Plantilla para activar ese workflow en cada repo (Actions → New workflow) |

GitHub usa estos archivos en cualquier repo de la org que no tenga los suyos. La guía «Empieza aquí» para miembros está en `.github-private` (solo la ven los miembros).

Cambiar `GOVERNANCE.md` requiere 2 owners; el resto, 1 aprobación.

## Licencia

[PolyForm Strict 1.0.0](LICENSE.md) © 2026 Luis Xavier García Pimentel Ascencio y Elyos Racing Team.
