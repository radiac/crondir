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

Add a cron snippet:

```bash
uvx crondir add path/to/definition
```

Remove a cron snippet:

```bash
uvx crondir remove definition
```

Build the crontab from current definitions:

```bash
uvx crondir build
```

Or if you don't have or want uv installed, you can use `pip`:

```bash
pip install crondir
crondir add path/to/definition
crondir remove path/to/definition
crondir build
```


For full command line options, see :doc:`commands`.
