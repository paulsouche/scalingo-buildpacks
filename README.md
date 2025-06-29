# Scalingo 24 Buildpack: Graphviz

Install [Graphviz](http://www.graphviz.org/) on Scalingo 24.

## Description

This buildpack installs Graphviz on Scalingo and makes it available to your application.

The Graphviz executables are installed to the following directory:

```
/app/.scalingo-buildpack-graphviz/usr/bin
```

The above directory is added to the `PATH` environment variable, so Graphviz commands like `dot` and `neato` are directly available to your app without specifying their path.

## Usage

For adding the buildpack in addition with other buildpacks, use: `https://github.com/paulsouche/scalingo-buildpacks#graphviz-24`

## Verify

After deploying your application with the buildpack at least once, you can verify the installation of Graphviz with:

```bash
scalingo -a <YOUR APPLICATION HERE> run dot -V
```

The above command runs `dot -V` on the application, that is, in the same environment in which your application is running. That means, if the above command succeeds, your application can use Graphviz commands such as `dot` in the same way.

## License

Licensed under the MIT License. See [LICENSE.md](LICENSE.md) file.
