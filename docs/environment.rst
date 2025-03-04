=====================
Environment variables
=====================


You can set the following environment variables:

``CRONDIR_PATH=<path>``:
  Change the default cron dir from ``~/.cron.d/``


``CRONDIR_BACKUP=<path>``:
  Change the default backup dir from ``~/.cron.d/backups/``


In most cases, these can be set in your ``.bashrc``::

    export CRONDIR_PATH=~/cron_dir/
