# Revisión del modelo histórico

El DBML de [schema/legacy-concept.dbml](../schema/legacy-concept.dbml) contiene 15 tablas y 16 referencias declaradas. Se conserva sin corregir para poder distinguir el diseño heredado de las decisiones futuras.

| Área | Tablas heredadas |
| --- | --- |
| Cuenta y catálogos | `users`, `genders`, `countries`, `user_statuses`, `timezones`, `languages` |
| Seguridad y actividad | `user_sessions`, `login_history`, `user_devices`, `password_history` |
| Contenido | `concepts`, `concept_translations`, `concept_image_assets`, `concept_relationships`, `relationship_types` |

El diseño representa un concepto independiente del idioma, sus traducciones y sus imágenes. La pronunciación aparece como forma fonética de texto; no hay tabla ni proceso de audio TTS.

## Huecos antes de crear migraciones

- No están modeladas las tarjetas vistas por cada usuario, respuestas de práctica, historial de repasos, último repaso, próximo repaso ni progreso SRS.
- La elección de pareja L1/L2 y las categorías mencionadas en notas de producto tampoco tienen representación completa.
- Hay claves foráneas con tipos incompatibles en el borrador: `users.id` es `bigint`, mientras varios `user_id` son `integer`; `languages.id` es `smallint`, mientras los idiomas asociados a `users` son `integer`.
- `genders.id` es `boolean`; conviene decidir si ese catálogo y otros datos personales son necesarios para el MVP.

Los dos archivos `.backup` y `schemas_public.pgerd` del origen describen estados anteriores y distintos. No se restauraron ni se copiaron a este repositorio. No debe generarse una migración a partir de ellos sin revisar primero su procedencia y contenido.
