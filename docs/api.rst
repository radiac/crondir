===
API
===

You can use crondir from your Python code

.. code-block:: python

    from crondir import Crondir

    crondir = Crondir(cron_dir="~/override_path/")

    print("Existing crontab:", crondir.read())

    print("Adding a snippet file")
    crondir.add_file(source_file, snippet="snippet1", force=True)

    print("Adding a snippet string")
    crondir.add_string(
        "0 * * * * /home/deploy/project/bin/hourly_refresh.sh",
        snippet="snippet2",
        force=True,
    )

    print("Removing files")
    crondir.remove("snippet1", force=True)
    crondir.remove("snippet2", force=True)

    print("Building")
    crondir.build()


API reference
=============

.. autoclass:: crondir.crondir.Crondir
	:members:
	:show-inheritance:
