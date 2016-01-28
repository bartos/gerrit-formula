gerrit
======

Formula to install and configure gerrit.

.. note::

    See the full `Salt Formulas installation and usage instructions
    <http://docs.saltstack.com/en/latest/topics/development/conventions/formulas.html>`_.

Available states
================

.. contents::
    :local:

``gerrit``
----------

Install gerrit and start up the gerrit service. (Currently tested under Ubuntu 14.04 LTS).

For a list of all available options, look at: `gerrit/defaults.yaml` - also have a look at the pillar.example and map.jinja.

Testing
=======

Not yet done.

Gerrit config customization
===========================

A configuration file is added as a file.managed in id: gerrit-copy-config in install.sls.
Config file should be a jinja template since we take a pillar with port number and put it into the final gerrit.config

Example gerrit.jinja is placed in example dirrectory.
Note that there is a jinja import in the header:
  
    {% from "gerrit/map.jinja" import gerrit_settings with context -%}

then, we can use port defined in pillar/gerrit.sls

    [httpd]
          listenUrl = http://*:{{ gerrit_settings.port }}/






