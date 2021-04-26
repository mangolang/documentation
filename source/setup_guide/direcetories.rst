
Directories and paths
===============================

Mango uses these directories:

Configuration directory
-------------------------------

This directory contains Mango configuration files.

.. todo: list of config files

The default locations are:

* Linux: `$HOME/.config/mango` (actually `$XDG_CONFIG_HOME/mango`), falling back to `$HOME/.mango/config`.
* Windows: `mango` inside `FOLDERID_RoamingAppData`, falling back to `.mango/cache` inside `FOLDERID_Profile`.
* MacOS: `$HOME/Library/Application Support/mango`, falling back to `$HOME/.mango/cache`.

The default location can be overwritten by setting `MANGO_USER_CONFIG_PATH`.

This directory should not take up much space. You should not delete it directory unless you want to reset Mango (or have uninstall it).

User cache directory
-------------------------------

A cache directory for cache shared between all projects a user has.

This contains things like:

* Artifacts from external dependencies (but not for project code).
* Mango compiler and daemon state.
* Lock files.

The default locations are:

* Linux: `$HOME/.cache/mango` (actually `$XDG_CACHE_HOME/mango`), falling back to `$HOME/.mango/cache`, or a temporary directory.
* Windows: `mango` inside `FOLDERID_LocalAppData`, falling back to `.mango/cache` inside `FOLDERID_Profile`, or a temporary directory.
* MacOS: `$HOME/Library/Caches/mango`, falling back to `$HOME/.mango/cache`, or a temporary directory.

The default location can be overwritten by setting `MANGO_USER_CACHE_PATH`.

It should be safe to delete this directory, but only if mango is not running. Doing so will make the next build(s) slower.

Project target directory
-------------------------------

This contains:

* Compiled binaries and libraries.
* Intermediary build output for project code (but perhaps not for external dependencies).
* Other build artifacts, like static resources.
* Compiler state information.

The default location is a directory `target` at the root of your project.

This default location can be overwritten by setting `MANGO_TARGET_DIR`. It should not be shared with other projects.

It should be safe to delete this directory, but only if mango is not running. Doing so will make the next build(s) slower.


