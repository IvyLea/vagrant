---
page_title: "Configuration- Docker Provider"
sidebar_current: "docker-configuration"
---

# Docker Configuration

The Docker provider has some provider-specific configuration options
you may set. A complete reference is shown below.

### Required

  * `build_dir` (string) - The path to a directory containing a Dockerfile.
    One of this or `image` is required.

  * `image` (string) - The image to launch, specified by the image ID or a name
    such as `ubuntu:12.04`. One of this or `build_dir` is required.

### Optional

  * `build_args` (array of strings) - Extra arguments to pass to
      `docker build` when `build_dir` is in use.

  * `cmd` (array of strings) - Custom command to run on the container.
    Example: `["ls", "/app"]`.

  * `create_args` (array of strings) - Additional arguments to pass to
    `docker run` when the container is started. This can be used to set
    parameters that aren't exposed via the Vagrantfile.

  * `env` (hash) - Environmental variables to expose into the container.

  * `expose` (array of integers) - Ports to expose from the container
    but not to the host machine. Useful for links.

  * `link` (method, string argument) - Link this container to another
    by name. Example: `docker.link("db")`.

  * `force_host_vm` (boolean) - If true, then a host VM will be spun up
    even if the computer running Vagrant supports Linux containers. This
    is useful to enforce a consistent environment to run Docker.

  * `has_ssh` (boolean) - If true, then Vagrant will support SSH with
    the container. This allows `vagrant ssh` to work, provisioners, etc.
    This defaults to false.

  * `host_vm_build_dir_options` (hash) - Synced folder options for the
    `build_dir`, since the build directory is synced using a synced folder
    if a host VM is in use.

  * `name` (string) - Name of the container. Note that this has to be unique
    across all containers on the host VM. By default Vagrant will generate
    some random name.

  * `ports` (array of strings) - Ports to expose from the container to the
    host. These should be in the format of `host:container`.

  * `remains_running` (boolean) - If true, Vagrant expects this container
    to remain running and will make sure that it does for a certain amount
    of time. If false, then Vagrant expects that this container will
    automatically stop at some point, and won't error if it sees it do that.

  * `vagrant_machine` (string) - The name of the Vagrant machine in the
    `vagrant_vagrantfile` to use as the host machine. This defaults to
    "default".

  * `vagrant_vagrantfile` (string) - Path to a Vagrantfile that contains
    the `vagrant_machine` to use as the host VM if needed.

  * `volumes` (array of strings) - List of directories to mount as
    volumes into the container. These directories must exist in the
    host where Docker is running. If you want to sync folders from the
    host Vagrant is running, just use synced folders.
