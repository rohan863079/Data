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

At the end, provide a clear PASS/FAIL report and identify any remaining OAuth scope, permission, or Free Edition 


limitations.


-----------
Databricks OAuth M2M, executor identity, Unity Catalog catalog/schema access, Volume metadata access, and Files API directory listing have all passed.

Now proceed with the next security and compatibility verification phase.

1. Review the complete Databricks remote execution implementation.
2. Verify that only the dedicated non-admin Service Principal "SQL-Practice-Studio-Executor" can be used by the backend.
3. Confirm that the old Admin Service Principal is never used for learner execution.
4. Review learner isolation, arbitrary code execution risks, access to other users' files, secrets exposure, timeouts, resource limits, cancellation, concurrency and log sanitization.
5. Verify whether Databricks Free Edition currently supports the required Jobs API and compute execution workflow.
6. Identify any blockers before a safe live test.

Important:

- Do not enable remote execution.
- Do not change readiness flags.
- Do not submit a live job yet.
- Do not deploy to production.
- Preserve the existing Local PySpark Runner.
- Do not expose credentials.

Return a detailed PASS/FAIL report and a list of remaining blockers.
