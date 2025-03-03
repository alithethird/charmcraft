HTTP Proxy
----------

Proxy settings should be set as model configurations. Charms generated
using the |extension_name| extension will make the Juju proxy
settings available as the ``HTTP_PROXY``, ``HTTPS_PROXY`` and
``NO_PROXY`` environment variables. For example, the ``juju-http-proxy``
environment variable will be exposed as ``HTTP_PROXY`` to the |framework|
service.

    See more: `Juju | List of model configuration
    keys <https://juju.is/docs/juju/list-of-model-configuration-keys>`_

