# Lexivela Domain

Este repositorio reúne el **diseño de datos y la futura persistencia** de Lexivela. El archivo [schema/legacy-concept.dbml](schema/legacy-concept.dbml) es una copia sin cambios del modelo conceptual más reciente de `flash_cards/SQL/01-database.sql`. Se cambió la extensión porque el contenido es DBML: **no se puede ejecutar como SQL ni usar como migración PostgreSQL**.

La [exportación PDF histórica](docs/legacy-schema.pdf) acompaña al modelo. No se ha comprobado que ambos artefactos representen exactamente la misma revisión.

## Estado

- Hay un modelo conceptual de cuentas, catálogos y contenido; [model-review.md](docs/model-review.md) resume su cobertura y sus huecos.
- Todavía no hay migraciones SQL, datos de prueba, esquema de estudio/SRS definitivo ni base de datos levantada por este repositorio.
- Los respaldos, configuraciones, scripts y Docker del origen permanecen en `flash_cards`. [El inventario histórico](docs/legacy-infrastructure.md) resume esos materiales sin copiar credenciales.

Las reglas de producto pertenecen a `lexivela`; la API deberá consumir el modelo de datos que se decida aquí. Antes de crear migraciones hay que reconciliar el DBML con el MVP definido en `lexivela/docs/mvp.md` y fijar una única fuente de verdad del esquema.
