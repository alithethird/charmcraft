Secrets
-------

Juju secrets can be passed as environment variables to your |framework| application. The
secret ID has to be passed to the application as a config option in the project file of
type ``secret``. This config option has to be populated with the secret ID, in the
format ``secret:<secret ID>``.

The environment variable name passed to the application will be:
