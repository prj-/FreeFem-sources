# FreeFEM Docker image

[FreeFEM](https://freefem.org) is an open-source partial differential equation solver for non-linear multi-physics problems in two and three dimensions.

## Usage

Run a FreeFEM script (bash/zsh):

```bash
docker run --rm -v $(pwd):/home/user freefem/freefem myScript.edp
```

PowerShell:

```powershell
docker run --rm -v ${PWD}:/home/user freefem/freefem myScript.edp
```

Run interactively:

```bash
docker run --rm -it -v $(pwd):/home/user freefem/freefem
```

Show the built-in help:

```bash
docker run --rm freefem/freefem --help
```

## MPI (parallel) usage

The image ships `FreeFem++-mpi` alongside the default `FreeFem++-nw` entry point.
To run an MPI job, override the entry point:

```bash
docker run --rm -v $(pwd):/home/user --entrypoint mpirun freefem/freefem \
  -np 4 /usr/local/bin/FreeFem++-mpi myScript.edp
```

## Image tags

| Tag | Description |
|-----|-------------|
| `latest` | Latest stable release (master branch) |
| `x.y` | Specific FreeFEM version (e.g. `4.16`) |

## Build information

Images are built automatically from the [FreeFem-sources](https://github.com/FreeFem/FreeFem-sources) repository on every version tag push.
The image is based on **Ubuntu 24.04** and installs FreeFEM from the official `.deb` package produced by the release workflow.

## Links

- [FreeFEM website](https://freefem.org)
- [Documentation](https://doc.freefem.org)
- [Source code](https://github.com/FreeFem/FreeFem-sources)
- [Issue tracker](https://github.com/FreeFem/FreeFem-sources/issues)
