# Main

This document outlines how a repository is exposed via an interface to be consumed by human and machine.

## Command

A command named `cri` must be available within your path/shell environment.

The following command **MUST** return an exitcode of 0:

```bash
$ command -v cri
```

That means that `cri` could potentially be defined as an executable file, a shell function, or an alias.

## Command Interface

The `cri` command at a minimum **MUST** support the following interface:

| Command       | Description                                    |
| ------------- | ---------------------------------------------- |
| `cri`         | Alias for `cri help`                           |
| `cri help`    | Prints interface usage documentation to stdout |
| `cri version` | Prints repository version to stdout            |

### Command: cri

Running `cri` without any parameters should be an alias for the `cri help` command and just display CLI usage documentation.

Example:

See the [cri help](#cri-help) documentation example below.

### Command: cri help

Running `cri help` should display CLI usage documentation. At a minimum this should include:

* List of all available commands
* Short summary for each available command

Example:

```bash
$ cri help
help                           Print CLI usage
version                        Print current version
```

### Command: cri version

Running `cri version` should display the current version of the repository. Repositories are free to store this value in any format/file they so choose based on language/tech being used.

For simple cases, we recommend using a file named `VERSION` in the root of the repository and following a pattern such as [Semantic Versioning](https://semver.org/) for releases.

Example:

```bash
$ cri version
0.0.1
```

## Conforming

That's it! _Technically_ that's all you need to implement to the common-repository-interface. However, the most basic case doesn't really do much of anything. We'll see in the other documents how the `cri` command can be augmented with extensions to gain much more.

## Extensions

Clearly you want more functionality that this, right? So do I! Take a look at the [Extensions](extensions.md)
document next to see how we can add/remove functionality via extensions!
