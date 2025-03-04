============
Contributing
============

Contributions are welcome, preferably via pull request. Check the github issues to see
what needs work, or if you have an idea for a new feature it may be worth raising an
issue to discuss it first.


Installing
==========

The easiest way to work on this is to fork the project on GitHub, then::

    git clone git@github.com:USERNAME/crondir.git
    cd crondir/
    uv venv .venv
    source .venv/bin/activate
    uv pip install -r tests/requirements.txt
    pre-commit install

(replacing ``USERNAME`` with your username).

This will install the development dependencies too.


Running locally
===============

You can now run the local crondir with::

    python -m crondir


Testing
=======

It's always easier to merge PRs when they come with tests.

Run the tests with pytest::

    pytest
