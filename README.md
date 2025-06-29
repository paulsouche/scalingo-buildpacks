# Scalingo 22 Buildpack: postgresql-autodoc

Install [postgresql-autodoc](https://github.com/cbbrowne/autodoc/) on Scalingo 22.

## Description

This buildpack installs postgresql-autodoc on Scalingo and makes it available to your application.

The postgresql-autodoc executables are installed to the following directory:

```
/app/.scalingo-buildpack-postgresql-autodoc/usr/bin
```

The above directory is added to the `PATH` environment variable, so postgresql_autodoc command is directly available to your app without specifying its path.

## Usage

For adding the buildpack in addition with other buildpacks, use: `https://github.com/paulsouche/scalingo-buildpacks#postgresql-autodoc-22`

## Verify

After deploying your application with the buildpack at least once, you can verify the installation of postgresql-autodoc with:

```bash
scalingo -a <YOUR APPLICATION HERE> run postgresql_autodoc --help
```

The above command runs `postgresql_autodoc --help` on the application, that is, in the same environment in which your application is running. That means, if the above command succeeds, your application can use postgresql-autodoc.

## License

Licensed under the MIT License. See [LICENSE.md](LICENSE.md) file.
