# Docker image build using bazel

This repo is an example of building a Docker image using bazel, intended for use with Gitpod.

It uses [bazelbuild/rules_docker](https://github.com/bazelbuild/rules_docker) and requires the docker
binary to be installed on the build machine, as the underlying functions in this example use the docker binary directly.

## Rules

* [rules_docker/package_managers](https://github.com/bazelbuild/rules_docker/tree/master/docker/package_managers)
    * Used to install packages via dpkg/apt
* [rules_docker/util](https://github.com/bazelbuild/rules_docker/blob/master/docker/util)
    * Used to configure Gitpod

## Minimum viable image

As described in the [Gitpod docs](https://www.gitpod.io/docs/configure/workspaces/workspace-image#custom-base-image),
the minimum viable image requires:

* `git`
* `git-lfs`
* `sudo`

Those binaries can be installed in the docker image in different ways, but for the sake of simplicity here we use the
available rules in `rules_docker`.

#### Gitpod user

The `gitpod` user and sudoers membership is required for Gitpod to function correctly. While it is possible to run a
workspace without the user and sudoers membership - it is not recommended as it will break certain features.

## Usage

Modify the `BUILD.bazel` accordingly and run:

```bash
bazel run :publish
```
