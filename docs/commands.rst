========
Commands
========

If using [uv](https://docs.astral.sh/uv/), add ``uvx`` to the start of the following
commands.

The ``crondir`` command supports the following operations:


``crondir build``
=================

Build the crontab from tasks in the cron dir::

    crondir build [--cron-dir=<path>] [--no-backup] [--backup-path=<path>]

where:

* ``--cron-dir=<path>`` - override the path to the cron dir, from ``~/.cron.d/``
* ``--no-backup`` - do not perform a backup
* ``--backup-path=<path>`` - override the path to the backup dir, from
  ``~/.cron.d/backups/``

You will need to run this command after you make any changes to the cron dir.

This will make a backup of this user's current crontab, then concatenate all snippets in
the cron dir, add any unmanaged existing crontab tasks, then install them as the new
crontab for this user.

Examples
--------

Backup and rebuild the crontab::

    crondir build

Rebuild without taking a backup::

    crondir build --no-backup

Instead of ``~/.cron.d/``, use the cron dir ``~/cron_tasks/``::

    crondir build --cron-dir=~/cron_tasks/


``crondir add``
===============

Add a cron snippet::

    crondir add <source> [<cron-name>] [--force] [--cron-dir=<path>]

where:

* ``<source>`` - the source file to install.
* ``<cron-name>`` - optional filename to give it in ``~/.cron.d/``. If not specified,
  will use the same filename as ``source``.
* ``--force`` - if the target already exists, overwrite it. If this is not set and it
  already exists, it will raise an error.
* ``--cron-dir=<path>`` - override the path to the cron dir, from ``~/.cron.d/``

You will need to run ``crondir build`` after this for your change to take effect.


Examples
--------

Add the file ``project/mytask`` as ``mytask``::

    crondir add project/mytask
    crondir build

Add the file ``project/mytask`` as ``project__mytask``::

    crondir add project/mytask project__mytask
    crondir build

Add the file ``project/mytask`` ``mytask`` and overwrite if it exists::

    crondir add project/mytask --force
    crondir build

Instead of ``~/.cron.d/``, use the cron dir ``~/cron_tasks/``::

    crondir add project/mytask --cron-dir=~/cron_tasks/
    crondir build --cron-dir=~/cron_tasks/


``crondir remove``
==================

Remove a cron snippet from the cron dir::

    crondir remove <cron-name> [--force] [--cron-dir=<path>]

where:

* ``<cron-name>`` - the cron name from ``crondir add`` - in other words, the filename in
  ``~/.cron.d/``.
  will use the same filename as ``source``.
* ``--force`` - if the target does not exists, don't report an error.
* ``--cron-dir=<path>`` - override the path to the cron dir, from ``~/.cron.d/``

You will need to run ``crondir build`` after this for your change to take effect.


Examples
--------

Remove the cron snippet named ``mytask``::

    crondir remove mytask
    crondir build


Try to remove ``mytask``, but don't fail if it isn't present::

    crondir remove mytask --force
    crondir build

Instead of ``~/.cron.d/``, use the cron dir ``~/cron_tasks/``::

    crondir remove mytask --cron-dir=~/cron_tasks/
    crondir build --cron-dir=~/cron_tasks/
