==========
Quickstart
==========

Installation
------------

Either install using ``pip``::

    pip install crondir

or run directly using [uv](https://docs.astral.sh/uv/) (recommended)::

    uvx crondir <command> [<options>]


Basic usage
-----------

Add a cron snippet::

  crondir add path/to/definition

Remove a cron snippet::

  crondir remove definition

List installed snippets::

  crondir list

Build the crontab from current snippets::

  crondir build

Or you may find it easier to skip the install step and run it using uv::

  uvx crondir add path/to/definition
  uvx crondir remove path/to/definition
  uvx crondir list
  uvx crondir build


For full command line options, see :doc:`commands`.
