# Creating Extensions

This document outlines how to create extensions that add subcommands to the `cri` command.

## Directory Structure

To create an extension, we need to create an extension directory as outlined in [extensions](extensions.md).

```bash
├── .cri
│   └── extensions
│       └── ${EXTENSION_NAME}
```

The following command **MUST** return an exitcode of 0:

```bash
$ test -d .cri/extensions/${EXTENSION_NAME}
```

## Extension Main

Each extension must also define a main/entrypoint file named `cri`. This file is invoked by the main `cri` command when the extension is invoked as a subcommand.

```
├── .cri
│   └── extensions
│       └── ${EXTENSION_NAME}
│           └── cri
```

The following command **MUST** return an exitcode of 0:

```bash
$ test -f .cri/extensions/${EXTENSION_NAME}/cri
```

Once this file exists, the extension should be automatically _registered_ to `cri` and accessible via a subcommand based on the extension name: `cri ${EXTENSION_NAME}`, e.g. `cri docker`.

## Extension Interface

The `cri ${EXTENSION_NAME}` command at a minimum **MUST** support the following interface:

| Command            | Description                                                                                     |
| ------------------ | ----------------------------------------------------------------------------------------------- |
| `cri ${EXTENSION_NAME}`         | Alias for `cri ${EXTENSION_NAME} help`                                             |
| `cri ${EXTENSION_NAME} help`    | Prints interface usage documentation to stdout for the `${EXTENSION_NAME}` command |

### Command: cri ${EXTENSION_NAME}

Running `cri ${EXTENSION_NAME}` without any parameters should be an alias for the `cri ${EXTENSION_NAME} help` command and just display CLI usage documentation.

Example:

See the `cri ${EXTENSION_NAME} help` documentation example below.

### Command: cri ${EXTENSION_NAME} help

Running `cri ${EXTENSION_NAME} help` should display CLI usage documentation. At a minimum this should include:

* List of all available commands
* Short summary for each available command

Example:

```bash
$ cri ${EXTENSION_NAME} help
help                           Print CLI usage
```

## Conforming

That's it! _Technically_, that's all you need to implement an extension. Create a named directory within `.cri/extensions`, add a `cri` entrypoint file and support the `help` command.

## Examples

Since this document just outlines the basic structure necessary to adding/creating a new extension, the next step should be to take a look at some examples that implement actual functionality.
