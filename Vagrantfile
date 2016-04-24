# -*- mode: ruby -*-
# vi: set ft=ruby :

# Set bluetooth dongle product and vendor ID.
BLUETOOTH_PRODUCT_ID = ENV.fetch("BLUETOOTH_PRODUCT_ID", "0x0001")
BLUETOOTH_VENDOR_ID = ENV.fetch("BLUETOOTH_VENDOR_ID", "0x0A12")

# Vagrantfile API/syntax version. Don"t touch unless you know what you"re doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/wily32"

  # Disable the new default behavior introduced in Vagrant 1.7, to
  # ensure that all Vagrant machines will use the same SSH key pair.
  # See https://github.com/mitchellh/vagrant/issues/5005
  config.ssh.insert_key = false

  # Load some provisioning scripts
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
  end

  # Configure usb autoconnect for bluetooth dongle
  # https://spin.atomicobject.com/2014/03/21/smartcard-virtualbox-vm/
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["usbfilter", "add", "0", "--target", :id, "--name", "bluetooth", "--vendorid", BLUETOOTH_VENDOR_ID, "--productid", BLUETOOTH_PRODUCT_ID]

  end
end
