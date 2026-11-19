# HomeTruth environment status

Confirmed by the owner on 19 November 2026: HomeTruth operates locally only.
There is no current hosted staging or production environment.

| Component | Current local location |
| --- | --- |
| Frontend | http://localhost:3000 |
| Backend API | http://localhost:8005 |
| MySQL | 127.0.0.1:3306, database `hometruth` |
| Qdrant | http://localhost:6333 |

The `-staging` repository folder names are historical. Old team IP addresses,
preview tunnels and deployment workflows do not identify current infrastructure.
GitHub main branches hold source code; merging a PR is not deployment. A React
production build is an optimised artifact, not a hosted production environment.

## Configuration

Keep local credentials in ignored backend `.env`. Frontend `.env` uses
`PORT=3000` and `REACT_APP_API_BASE_URL=http://localhost:8005`. Development-specific
frontend env files and shell values can override these settings. Never copy
backend credentials into frontend configuration. Preserve existing credentials
when adopting `.env.example` from a new checkout.

HT-301 removes obsolete staging commands and endpoints in backend PR 15 and
frontend PR 17. Those code changes require PR merge before they become main.
The active local frontend env files have already been corrected and its retired
`.env_staging` file removed. No database changes are part of this cleanup.

## Database and future hosting

Sequelize migrations manage the MySQL schema; automatic schema sync stays off.
HT-355 has been migrated and smoke-tested locally. No remote migration is owed
because no current remote environment exists. Recheck migration status whenever
code changes; a historical migration count is not a permanent assertion.

When hosting is introduced, first choose explicit server/database destinations
and separate credentials. Decide whether to seed fresh demo data or copy local
data. Back up MySQL, uploaded documents and relevant Qdrant storage; prove a
restore works before migrating a copy. For an existing populated destination,
rehearse all pending migrations, pause writes for the final backup and migration,
compare retained records, then smoke-test before reopening writes. HT-355 is
forward-only; recovery needs a verified backup and must account for later writes.
Never overwrite the original local data as part of provisioning hosting.
