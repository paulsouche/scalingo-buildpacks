# Scalingo buildpacks

This repository contains scalingo buildpacks to install binary dependencies that would normally be installed with `apt`.

## Forewords

### Purpose

Usually, one would just use `apt install`, however, this might don't work here, because some packages need to be installed to a custom directory in the application slug, and it's not possible to configure this with `apt`.

To work around this, the buildpack downloads all the required packages and installs them manually with `dpkg`.

### Get list of packages

The required packages include not only the binary but also all of its dependencies, and dependencies of dependencies, etc. Furthermore, some of the dependent packages might be already installed on the system, so they don't need to be installed.

This can quickly get complicated, so the best way is to let `apt` figure out the concrete set of packages to install for a specific Scalingo stack.

You can achieve that by running

```bash
scalingo -a <YOUR APPLICATION HERE> run apt install -y --print-uris <YOUR PACKAGE HERE> | grep http | awk '{print $1}' | tr -d "'"
```

This prints the URLs of the packages that `apt install` would install on this specific system.

This list can then be used in the `bin/compile` script for the corresponding Scalingo stack.

By installing precisely this set of packages, as figured out by `apt`, the effect should be the same as running `apt install`.

## Available packages

### graphviz

[graphviz](https://graphviz.org/) is available in this repository.
 - For a scalingo stack 22, please checkout the [graphviz-22](https://github.com/paulsouche/scalingo-buildpacks/tree/graphviz-22) branch.
 - For a scalingo stack 24, please checkout the [graphviz-24](https://github.com/paulsouche/scalingo-buildpacks/tree/graphviz-24) branch.

### postgresql-autodoc

[postgresql-autodoc](https://github.com/cbbrowne/autodoc) is available in this repository.
 - For a scalingo stack 22, please checkout the [postgresql-autodoc-22](https://github.com/paulsouche/scalingo-buildpacks/tree/postgresql-autodoc-22) branch.
 - For a scalingo stack 24, please checkout the [postgresql-autodoc-24](https://github.com/paulsouche/scalingo-buildpacks/tree/postgresql-autodoc-24) branch.

## License

Licensed under the MIT License. See [LICENSE.md](LICENSE.md) file.
