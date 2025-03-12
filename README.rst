Badges  plugin for `Tutor <https://docs.tutor.edly.io>`__
##################################################################

Tutor plugin that adds and configuring features for sharing to different "providers":
  - `Verifiable Credentials <https://edx-credentials.readthedocs.io/en/latest/verifiable_credentials/overview.html#>`__ with different credential stores that support standards like VC1.1, OBv3 such as `LCWallet <https://lcw.app/>`__ for example.
     - program certificate
     - course certificate
  - Badges:
     - `Credly <https://info.credly.com/>`__
     - `Accredible <https://www.accredible.com/>`__

The plugin also configures event buse between Credentials and LMS/CMS services.

    .. image:: docs/_images/interaction_diagram.svg
        :alt: Interaction diagram for receiving badges.


Installation
************

This tutor plugin interacts with the Credentials service, respectively,
one of its dependencies is the `tutor-credentials <https://github.com/overhangio/tutor-credentials/tree/release>`__
plugin, which must also be installed.
The following section will be changed after the Teak release.

.. code-block:: bash

    pipenv install git+https://github.com/overhangio/tutor-credentials.git@main
    pipenv install git+https://github.com/raccoongang/tutor-contrib-badges@main

Sample Pipfile for a complete Tutor Nightly installation
********************************************************

.. code-block:: toml

    [[source]]
    url = "https://pypi.org/simple"
    verify_ssl = true
    name = "pypi"
    
    [packages]
    tutor = {git = "https://github.com/overhangio/tutor.git@main"}
    tutor-mfe = {git = "https://github.com/overhangio/tutor-mfe.git@main"}
    tutor-discovery = {git = "https://github.com/overhangio/tutor-discovery.git@main"}
    tutor-credentials = {git = "https://github.com/overhangio/tutor-credentials.git@main"}
    tutor-contrib-badges = {git = "https://github.com/raccoongang/tutor-contrib-badges@main"}
    
    [dev-packages]
    
    [requires]
    python_version = "3.10"


Installation with Pipenv
========================

.. code-block:: bash

    pipenv install

Usage
*****

.. code-block:: bash

    tutor plugins enable mfe
    tutor plugins enable credentials
    tutor plugins enable discovery
    tutor plugins enable badges
    tutor images build openedx discovery credentials
    tutor local launch

The following additional services are added:

- credentials-eventbus-consumer
- credentials-certificates-eventbus-consumer
- tutor local start lms-eventbus-consumer
- tutor local start cms-eventbus-consumer

The services are started automatically but you can run it manually with the following commands:

.. code-block:: bash

    tutor local start credentials-eventbus-consumer -d
    tutor local start credentials-certificates-eventbus-consumer -d
    tutor local start lms-eventbus-consumer -d
    tutor local start cms-eventbus-consumer -d
    tutor local start credentials -d

Status
******
The plugin currently works with master Open edX platform and Tutor Nightly version accordingly.
Do not use the plugin with Sumac release. The plugin is going to be updated to the Teak release in April 20205.

License
*******

This software is licensed under the terms of the AGPLv3.
