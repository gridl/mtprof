mtprof
======

A multi-thread aware profiler package, with an API similar to that
of the standard ``cProfile`` module.  Profiling data generated by
``mtprof`` is in the same format as that generated by ``cProfile``
and can therefore be analyzed using the same tools (such as ``pstats``,
``snakeviz``, etc.).

Compatibility
-------------

Python 3 is required, and only POSIX systems (Linux, etc.) are currently
supported.

Install
-------

This is a pure Python package, so ``pip install mtprof`` should generally
work everywhere.

Command-line interface
----------------------

``python -m mtprof`` provides an interface similar to ``python -m cProfile``
and allows you to profile scripts, modules or entire applications.

Python API
----------

The ``mtprof.Profile`` class has an API similar to ``cProfile.Profile``.

Limitations
-----------

Due to the way Python profiling works, ``mtprof`` is only able to exploit
profiling stats from threads whose lifetime is a subset of the profiler's
lifetime.  A thread started before profiling was started, or ended after
profiling was stopped, cannot have its statistics collected.

Due to this limitation, it is probably easier to use the command-line
interface, which is similar to that of ``cProfile``: just run
``python -m mtprof --help`` to get a view of the available options.

Only threads created using the standard ``threading.Thread`` interface
are recognized.  For most use cases this should not be an issue.

Status
------

This package is experimental.
