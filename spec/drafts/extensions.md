# Extensions

This document outlines the mechanism to add arbitrary functionality to the `cri` command.

## Directory Structure

The repository must contain a `.cri` directory within the root of the repository.

The following command **MUST** return an exitcode of 0:

```bash
$ test -d .cri
```

Within the `.cri` directory there is a single directory named `extensions`.

```bash
.
├── .cri
│   └── extensions
```

The following command **MUST** return an exitcode of 0:

```bash
$ test -d .cri/extensions
```

Within the `.cri/extensions` directory there should be one or more directories, each named based on what extension functionality they're adding. For example, if we wanted to add support for [msbuild](https://github.com/Microsoft/msbuild) related commands, we'd likely name the directory `msbuild`.

The following names are **RESERVED** and disallowed from being used:

* `cri`
* `help`
* `usage`
* `version`

From here, the layout/requirements will be easier to see by viewing actual examples.
