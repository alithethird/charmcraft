.. _go-framework-extension:

.. |base_url| replace:: ``APP_BASE_URL``

.. |juju_integrate_postgresql| replace:: ``juju go <go charm> postgresql``

.. |framework| replace:: Go

.. |extension_name| replace:: ``go-framework``

Go framework extension
======================

.. include:: /reuse/reference/extensions/extension_title.rst


``charmcraft.yaml`` > ``config`` > ``options``
----------------------------------------------

You can use the predefined options (run ``charmcraft expand-extensions`` for details)
but also add your own, as needed.

The predefined configuration options for the ``go-framework`` are: - **app-port**: Port
in which the application should listen. The ingress will be configured using this port.
The environment variable passed to the app is ``APP_PORT``. Default value is 8080. -
**app-secret-key**: Long secret you can use for sessions, csrf or any other thing where
you need a random secret shared by all units. The environment variable passed to the app
is ``APP_METRICS_PORT``. The default value is random. - **metrics-port**: Port where the
prometheus metrics will be scraped. The environment variable passed to the app is
``APP_PORT``. Default value is 8080. - **metrics-path**: Path where the prometheus
metrics will be scraped. The environment variable passed to the app is
``APP_METRICS_PATH``. Default value is ``/metrics``.

In case you want to add extra configuration options, any option you define will be used
to generate environment variables; a user-defined option ``config-option-name`` will
generate an environment variable named ``APP_CONFIG_OPTION_NAME`` where the option name
is converted to upper case and dashes are converted to underscores.

In either case, you will be able to set it in the usual way by running ``juju config
<application> <option>=<value>``. For example, if you define an option called ``token``,
as below, this will generate a ``APP_TOKEN`` environment variable, and a user of your
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

    juju integrate go-k8s grafana
    juju integrate go-k8s loki
    juju integrate go-k8s prometheus

.. include:: /reuse/reference/extensions/observability_2.rst

.. include:: /reuse/reference/extensions/secrets_1.rst

.. code-block:: bash

    APP_<config option name>_<key inside the secret>

.. include:: /reuse/reference/extensions/secrets_2.rst