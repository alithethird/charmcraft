.. _fastapi-framework-extension:

.. |base_url| replace:: ``APP_BASE_URL``

.. |juju_integrate_postgresql| replace:: ``juju integrate <fastapi charm> postgresql``

.. |framework| replace:: FastAPI

.. |extension_name| replace:: ``fastapi-framework``

FastAPI framework extension
===========================

.. include:: /reuse/reference/extensions/extension_title.rst


``charmcraft.yaml`` > ``config`` > ``options``
----------------------------------------------

You can use the predefined options (run ``charmcraft expand-extensions``
for details) but also add your own, as needed.

In the latter case, any option you define will be used to generate
environment variables; a user-defined option ``config-option-name`` will
generate an environment variable named ``APP_CONFIG_OPTION_NAME`` where
the option name is converted to upper case, dashes will be converted to
underscores and the ``APP_`` prefix will be added.

In either case, you will be able to set it in the usual way by running
``juju config <application> <option>=<value>``. For example, if you
define an option called ``token``, as below, this will generate a
``APP_TOKEN`` environment variable, and a user of your charm can set it
by running ``juju config <application> token=<token>``.

.. code-block:: yaml

    config:
      options:
        token:
          description: The token for the service.
          type: string
          optional: false

.. include:: /reuse/reference/extensions/non_optional_config.rst

.. include:: /reuse/reference/extensions/integrations.rst

.. include:: /reuse/reference/extensions/http_proxy.rst

.. include:: /reuse/reference/extensions/background_tasks.rst

.. include:: /reuse/reference/extensions/observability_1.rst

.. code-block:: bash

    juju integrate fastapi-k8s grafana
    juju integrate fastapi-k8s loki
    juju integrate fastapi-k8s prometheus

.. include:: /reuse/reference/extensions/observability_2.rst

.. include:: /reuse/reference/extensions/migrate_sh.rst

.. include:: /reuse/reference/extensions/secrets_1.rst

.. code-block:: bash

    APP_<config option name>_<key inside the secret>

.. include:: /reuse/reference/extensions/secrets_2.rst