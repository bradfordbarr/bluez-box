# bluez-box

This is my development box for working with BlueZ. Base image is Ubuntu 15.04
LTS. BlueZ 5.x requires systemd to support all of its tools. Ubuntu 15.04 was
the first Ubuntu release to support BlueZ 5.x out of the box.

## Getting Started

To get started, do the default vagrant dance.

```sh
$ vagrant up
$ vagrant provision
$ vagrant ssh
```

There should be a `bluez` directory in your home.
