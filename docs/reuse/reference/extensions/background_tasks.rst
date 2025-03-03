Background Tasks
----------------

Extra services defined in the file
:external+rockcraft:ref:`rockcraft.yaml <rockcraft.yaml_reference>`
with names ending in ``-worker`` or ``-scheduler`` will be passed the same environment
variables as the main application. If there is more than one unit in the application,
the services with the name ending in ``-worker`` will run in all units. The services
with name ending in ``-scheduler`` will only run in one of the units of the application.
