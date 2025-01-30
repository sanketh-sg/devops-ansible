Once you've decided to use vagrant with docker, the main obstacle is that you have to provide your own base box. This is a box that is running a ssh server, with a vagrant user authenticated with vagrant's key pair, and passwordless sudo. Vagrant uses a Dockerfile to build this. In a Dockerfile adjacent my Vagrantfile,

The other tricky bit is that in order for systemd, the init implementation used in the Linux distribution, to run inside our container, we have to expose a few filesystems by passing them to the docker run command. In Vagrantfile, Vagrant will use these arguments when invoking docker run --tmpfs /tmp:exec ...  If you don't expose these directories, systemd will not be able to start any services, including the ssh server.

[text](https://dev.to/dholth/how-to-use-docker-instead-of-virtualbox-on-osx-without-changing-the-world-4ack)

