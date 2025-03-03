.. _django-framework-extension:

.. |base_url| replace:: ``DJANGO_BASE_URL``

.. |juju_integrate_postgresql| replace:: ``juju integrate <django charm> postgresql``

.. |framework| replace:: Django

.. |extension_name| replace:: ``django-framework``


Django framework extension
==========================

.. include:: /reuse/reference/extensions/extension_title.rst


Database requirement
--------------------

Django requires a database to function. When generating a new project,
the default is to make use of `SQLite <https://www.sqlite.org/>`_.
Using SQLite is not recommended for production, especially on Kubernetes
deployments, because the database is not shared across units and any
contents will be removed upon a new container being deployed. The
``django-framework`` extension therefore requires a database integration
for every application, such as
`PostgreSQL <https://www.postgresql.org/>`_ or
`MySQL <https://www.mysql.com/>`_. See the
:ref:`how-to guide <manage-12-factor-app-charms>` for how to deploy
a database and integrate the Django application with it.


``config.options`` key
----------------------

You can use the predefined options (run ``charmcraft expand-extensions``
for details) but also add your own, as needed.

In the latter case, any option you define will be used to generate
environment variables; a user-defined option ``config-option-name`` will
generate an environment variable named ``DJANGO_CONFIG_OPTION_NAME``
where the option name is converted to upper case, dashes will be
converted to underscores and the ``DJANGO_`` prefix will be added.

In either case, you will be able to set it in the usual way by running
``juju config <application> <option>=<value>``. For example, if you
define an option called ``token``, as below, this will generate a
``DJANGO_TOKEN`` environment variable, and a user of your charm can set
it by running ``juju config <application> token=<token>``.

.. code-block:: yaml

    config:
      options:
        token:
          description: The token for the service.
          type: string

For the predefined configuration option ``django-allowed-hosts``, that
will set the ``DJANGO_ALLOWED_HOSTS`` environment variable, the ingress
URL or the Kubernetes service URL if there is no ingress integration,
will be set automatically.

.. include:: /reuse/reference/extensions/non_optional_config.rst


.. include:: /reuse/reference/extensions/integrations.rst

.. include:: /reuse/reference/extensions/http_proxy.rst

.. include:: /reuse/reference/extensions/background_tasks.rst

.. include:: /reuse/reference/extensions/observability_1.rst

.. code-block:: bash

    juju integrate django-k8s grafana
    juju integrate django-k8s loki
    juju integrate django-k8s prometheus

.. include:: /reuse/reference/extensions/observability_2.rst

.. include:: /reuse/reference/extensions/secrets_1.rst

.. code-block:: bash

    DJANGO_<config option name>_<key inside the secret>

.. include:: /reuse/reference/extensions/secrets_2.rst