# Reference Implementation

This document outlines a reference implementation of `cri` using [Make](https://en.wikipedia.org/wiki/Make_(software)).

## Command

If we're using `make` and a `Makefile` to define our `cri` interface, we need to add an alias to our shell environment.

```bash
$ tail -n1 ~/.zshrc
alias cri=make
```

```bash
$ command -v cri
cri: aliased to make
```

## Command Interface

In order to implement the main interface, our `Makefile` is implemented as:

```bash
$ cat Makefile
.DEFAULT_GOAL := help

help: usage  ## Print CLI usage

version:  ## Print current version
	@cat VERSION

.PHONY: usage
usage:
	@awk 'BEGIN {FS = ":.*?## "} /^[%a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST) | sort
```
