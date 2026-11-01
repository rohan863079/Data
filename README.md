# Data

The Databricks Unity Catalog permissions have now been granted to the new non-admin Service Principal "SQL-Practice-Studio-Executor".

Granted permissions:

- Catalog "workspace": USE CATALOG
- Schema "workspace.default": USE SCHEMA
- Volume "workspace.default.practice_files": READ VOLUME
- WRITE VOLUME if required by the upload workflow

Please perform a fresh, read-only verification using the existing backend ".env" configuration.

1. Verify OAuth M2M token generation separately from subsequent API calls.
2. Verify the authenticated Service Principal identity, if the supported API allows it.
3. Test access to catalog "workspace".
4. Test access to schema "workspace.default".
5. Test access to the Volume "practice_files" using the correct Unity Catalog Volume API, not a table API.
6. Test listing the Volume contents using the appropriate API.
7. Report the exact HTTP status and sanitized error message for each check.

Important:

- Do not print or expose Client Secret, access tokens, or other credentials.
- Do not use the old Admin Service Principal.
- Do not submit learner code or execute a Databricks job.
- Do not enable remote execution or change readiness flags.
- Do not deploy to production.
- Keep the existing Local PySpark Runner working.

At the end, provide a clear PASS/FAIL report and identify any remaining OAuth scope, permission, or Free Edition limitations.
