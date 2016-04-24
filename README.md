# bluez-box

This is my development box for working with BlueZ. Base image is Ubuntu 15.04
LTS. BlueZ 5.x requires systemd to support all of its tools. Ubuntu 15.04 was
the first Ubuntu release to support BlueZ 5.x out of the box.

## Prerequisites

To follow with the BlueZ 5.x introduction series you will need a bluetooth
dongle that can support Bluetooth 4.0. I am using [these][1]. If you do
use the same dongle as I am everything should already be configured for you.

If you are not using the same Bluetooth 4.0 dongle as I am you will need to
know your dongle's product and vendor IDs are. To figure out what your product
and vendor IDs are use `lsusb` in Linux, or check usb in System Information on
a Mac (I don't know how to find that info on Windows).

Once you've found your product and vendor IDs, you'll need to export them as
environment variables (replace `XXXX` with your ID in hex).

```sh
$ export BLUETOOTH_PRODUCT_ID='0xXXXX'
$ export BLUETOOTH_VENDOR_ID='0xXXXX'
```

## Getting Started

To get started, do the the following. The `vagrant reload` command is required
to load a new kernel.

```sh
$ vagrant up
$ vagrant provision
$ vagrant reload
$ vagrant ssh
```

There should be a `bluez` directory in your home.

[1]: http://www.amazon.com/BATTOP-Bluetooth-Dongle-Receiver-Chipset/dp/B00IMALQ94
