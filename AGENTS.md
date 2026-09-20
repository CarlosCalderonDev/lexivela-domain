# Instrucciones para agentes

## Propósito y estado

Este repositorio es responsable del diseño de datos y de las futuras migraciones de Lexivela. `schema/legacy-concept.dbml` es una copia histórica de DBML, aunque su origen terminaba en `.sql`. No es SQL ejecutable ni una migración PostgreSQL.

## Límites

- Lee `README.md` y `docs/model-review.md` antes de modificar el modelo. Confronta cualquier propuesta nueva con las reglas del MVP de `lexivela`.
- No alteres el DBML histórico para ocultar problemas heredados; crea una revisión nueva cuando se acuerde el esquema definitivo.
- No restaures respaldos ni sustituyas bases de datos como comprobación rutinaria. Los respaldos y configuraciones antiguas siguen en `flash_cards` y pueden contener datos o credenciales sensibles.
- Las migraciones futuras y la configuración de persistencia pertenecen aquí; el transporte HTTP pertenece a `lexivela-api`.

## Forma de trabajo

- Revisa `git status` y conserva cambios locales del usuario.
- Redacta documentación en español, identificadores de código en inglés y comentarios de código en español.
- Verifica el formato real de cada archivo antes de ejecutarlo. Usa `tmp/` para archivos descartables; su contenido queda ignorado por Git.

## Publicación obligatoria de cambios de IA

- Trabaja exclusivamente en la rama `agents`. Antes de editar, cámbiate a ella; si todavía no existe, créala. No edites, confirmes, fusiones ni subas cambios desde `main`, `develo` u otra rama.
- Al terminar cada cambio coherente, revisa el diff y añade solo los archivos modificados por la IA. Crea un commit con un mensaje específico en español, por ejemplo `docs(datos): aclarar el estado del esquema`; explica el motivo en el cuerpo cuando haga falta. No uses mensajes genéricos.
- Sube cada commit al remoto con `git push -u origin agents` la primera vez y `git push origin agents` después. Comprueba el resultado y comunica el identificador del commit.
- Si el remoto no está disponible o el push falla, conserva el commit local e informa el bloqueo. No publiques en otra rama para evitarlo.
