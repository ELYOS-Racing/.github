# Cómo contribuir

Guía general para todos los repos de [`ELYOS-Racing`](https://github.com/ELYOS-Racing). Si un repo tiene su propio `CONTRIBUTING.md`, ese manda en lo que difiera. Las reglas de fondo están en [`GOVERNANCE.md`](GOVERNANCE.md).

## Flujo: issue → rama → PR

1. **Issue.** Todo trabajo empieza en un issue, con el formulario que corresponda (tarea o bug). Elige el área en el desplegable: el issue se etiqueta solo con `area:*`.
2. **Rama.** `<tipo>/<issue>-<descripción>` desde `main`:

   | Tipo | Para |
   |---|---|
   | `feat/` | Funcionalidad nueva |
   | `fix/` | Corrección |
   | `docs/` | Solo documentación |
   | `refactor/` | Reorganizar sin cambiar comportamiento |
   | `test/` | Pruebas |
   | `chore/` | Mantenimiento (CI, dependencias, estructura) |
   | `release/` | Solo en las semanas previas a una competencia (`release/2027-indy`) |

   Ejemplo: `feat/42-encoder-foc`.
3. **Commits.** `<área>: <qué>`, en español, en imperativo o presente, y **firmados con DCO** (`git commit -s`, agrega `Signed-off-by`).

   ```text
   driver: sincroniza lectura de corriente con PWM
   ```

4. **PR.** Llena la plantilla (qué cambia y cómo se probó), enlaza el issue (`Closes #42`) y espera CI en verde.
   - Si eres **contribuidor calificado** de tu área, puedes hacer merge de tu propio PR.
   - Si no, pide la aprobación de un calificado de tu área.
   - `safety-critical`: enlaza la sesión de banco o abre un issue `test-pending`.
5. **Merge.** La rama se borra.

## Bloqueos entre áreas

Si tu issue espera a otro (de tu repo o de otra área), márcalo en el issue que espera: **Relationships → Mark as blocked by**. Si lo que bloquea es una interfaz (pinout, barrenos, conector), el issue bloqueante es "ICD aprobado" en `sys-integration/interfaces/`.

## Etiquetas

| Prefijo | Valores | Uso |
|---|---|---|
| `area:` | Por repo (`area:driver`, `area:telemetry`, `area:control`…) | Qué parte toca |
| `type:` | `feature`, `fix`, `refactor`, `review`, `test` | Qué clase de trabajo es |
| `prio:` | `p0` (ya) · `p1` (próximo hito) · `p2` · `p3` | Urgencia |
| `vehicle:` | `proto`, `adc` | A qué vehículo aplica |
| Especiales | `safety-critical`, `good-first-issue`, `critical-path`, `optional` | — |

## Pruebas

Todo PR con lógica nueva trae su prueba; el CI en verde es requisito de merge. La lógica que no depende del hardware va en `lib/` para que compile en el entorno `native` de PlatformIO.

## Herramientas

- **Firmware:** PlatformIO (VS Code). En Windows, clona en una ruta corta (por ejemplo `C:\w\`): las rutas largas rompen la compilación.
- **Quien no programa** (mecánica, electrónica, ops): GitHub Desktop.
- **CAD:** los archivos nativos de SolidWorks viven en SharePoint; en GitHub solo van texto y releases con STEP/PDF/DXF.

## Dudas

Pregunta en el issue o en el canal de tu área. Para pedir acceso, abre un issue en `ops-tasks`.
