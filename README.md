# crondir

[![PyPI](https://img.shields.io/pypi/v/crondir.svg)](https://pypi.org/project/crondir/)
[![Documentation](https://readthedocs.org/projects/crondir/badge/?version=latest)](https://crondir.readthedocs.io/en/latest/)
[![Tests](https://github.com/radiac/crondir/actions/workflows/ci.yml/badge.svg)](https://github.com/radiac/crondir/actions/workflows/ci.yml)
[![Coverage](https://codecov.io/gh/radiac/crondir/branch/main/graph/badge.svg?token=BCNM45T6GI)](https://codecov.io/gh/radiac/crondir)

Manage your user crontab with a cron.d directory in your home.

Simplifies the automated management of cron tasks in the user space. Snippets are
concatenated from your cron.d into the crontab.

- Store and manages crontab definitions in separate files
- Does not interfere with existing crontab entries
- Backs up crontab each time it builds
- Everything configurable

## Usage

Recommended use is with [uv](https://docs.astral.sh/uv/).

Add a cron snippet:

```bash
uvx crondir add path/to/snippet_name
```

Remove a cron snippet:

```bash
uvx crondir remove snippet_name
```

List installed cron snippets:

```bash
uvx crondir list
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

By default, crondir stores crontab definitions in `~/.cron.d/`, and creates backups
in `~/.cron.d/backups/`.

For full command line options, see [command documentation](https://crondir.readthedocs.io/en/latest/)

## Example

Lets say we're deploying a project with an hourly cron task, and will be running it from
a `deploy` user. Our project is at `/home/deploy/project/`

Create a file in our project, `cron_task`

```
0 * * * * /home/deploy/project/bin/hourly_refresh.sh
```

To add this task, run:

```bash
cd ~
uvx crondir add project/cron_task project_hourly
uvx crondir build
```

This will:

- create the dir `~/.cron.d/`
- copy `project/cron_task` into `~/.cron.d/` as `~/.cron.d/project_hourly`
- rebuild the crontab to include the lines from `~/.cron.d/project_hourly`

If we want the task to stop, we can run:

```bash
cd ~
uvx crondir remove project_hourly
uvx crondir build
```

This will

- remove the file `~/.cron.d/project_hourly`
- rebuild the crontab

Files in `~/cron.d` can also be manually added and removed.
