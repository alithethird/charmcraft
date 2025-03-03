.. _flask-framework-extension:

.. |base_url| replace:: ``FLASK_BASE_URL``

.. |juju_integrate_postgresql| replace:: ``juju go <flask charm> postgresql``

.. |framework| replace:: Flask

.. |extension_name| replace:: ``flask-framework``


Flask framework extension
=========================

.. include:: /reuse/reference/extensions/extension_title.rst


``charmcraft.yaml`` > ``config`` > ``options``
----------------------------------------------

You can use the predefined options (run ``charmcraft expand-extensions`` for details)
but also add your own, as needed.

In the latter case, any option you define will be used to generate environment
variables; a user-defined option ``config-option-name`` will generate an environment
variable named ``FLASK_CONFIG_OPTION_NAME`` where the option name is converted to upper
case and dashes are converted to underscores.

In either case, you will be able to set it in the usual way by running ``juju config
<application> <option>=<value>``. For example, if you define an option called ``token``,
as below, this will generate a ``FLASK_TOKEN`` environment variable, and a user of your
charm can set it by running ``juju config <application> token=<token>``.

.. code-block:: yaml

    config:
      options:
        token:
          description: The token for the service.
          type: string

.. include:: /reuse/reference/extensions/non_optional_config.rst

.. include:: /reuse/reference/extensions/integrations.rst

.. include:: /reuse/reference/extensions/http_proxy.rst

.. include:: /reuse/reference/extensions/background_tasks.rst

.. include:: /reuse/reference/extensions/observability_1.rst

.. code-block:: bash

    juju integrate flask-k8s grafana
    juju integrate flask-k8s loki
    juju integrate flask-k8s prometheus

.. include:: /reuse/reference/extensions/observability_2.rst

.. include:: /reuse/reference/extensions/migrate_sh.rst

.. include:: /reuse/reference/extensions/secrets_1.rst

.. code-block:: bash

    FLASK_<config option name>_<key inside the secret>

.. include:: /reuse/reference/extensions/secrets_2.rst
