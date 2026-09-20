# Inventario histórico de persistencia

Los archivos de infraestructura de `flash_cards` pertenecen a varias etapas del proyecto. Este resumen conserva su función sin copiar configuraciones ni credenciales a `lexivela-domain`.

| Archivo del origen | Estado observado |
| --- | --- |
| `docker/Dockerfile` | Define una imagen PostgreSQL 16 con configuración propia. |
| `docker/docker-compose.yml` | Utiliza la imagen oficial PostgreSQL 16 y publica el puerto local 5433 hacia 5432 del contenedor. No construye el Dockerfile ni importa el DBML. |
| `docs/03-docker.md` | Mezcla comandos para las dos configuraciones anteriores. No demuestra un servicio de aplicación operativo. |
| `configs/postgresql.conf`, `configs/*.conf` | Instantáneas de configuración local; `pgpass.conf` contiene credenciales. |
| `scripts/manage-db.ps1` | Gestiona una instalación local PostgreSQL 17 y usa parámetros diferentes a Compose. |
| `backups/*.backup` | Dos volcados históricos, de julio y diciembre de 2025, con modelos distintos al DBML actual. |
| `backups/schemas_public.pgerd` | Diagrama de un estado anterior del esquema. |

No se ha restaurado ningún respaldo ni ejecutado ninguna migración. Antes de crear un entorno nuevo hay que decidir el esquema de referencia, revisar la compatibilidad con el MVP y sustituir cualquier credencial heredada por variables de entorno o secretos locales fuera de Git.
