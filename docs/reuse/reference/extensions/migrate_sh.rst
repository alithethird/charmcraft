Regarding the ``migrate.sh`` file
---------------------------------

If your app depends on a database it is common to run a database
migration script before app startup which, for example, creates or
modifies tables. This can be done by including the ``migrate.sh`` script
in the root of your project. It will be executed with the same
environment variables and context as the |framework| application.

If the migration script fails, the app won't be started and the app
charm will go into blocked state. The migration script will be run on
every unit and it is assumed that it is idempotent (can be run multiple
times) and that it can be run on multiple units at the same time without
causing issues. This can be achieved by, for example, locking any tables
during the migration.