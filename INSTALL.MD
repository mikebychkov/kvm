
KVM - List OS Variants
=

When creating a guest with virt-install you need to specify the –os-variant.

To get a list of acceptable values, first install the libosinfo-bin package

sudo apt install libosinfo-bin

before running the command below:

osinfo-query os


Install KVM on Ubuntu
=

Step 1: Install the required packages
-
sudo apt -y install bridge-utils cpu-checker libvirt-clients libvirt-daemon qemu qemu-kvm

Execute the following command to make sure your processor supports virtualisation capabilities:

kvm-ok

Step 2: Check Virtualization Support on Ubuntu
-
1. Use the egrep command to check if your CPU supports hardware virtualization. Run the following command:

egrep -c '(vmx|svm)' /proc/cpuinfo

If the command returns a value of 0, your processor is not capable of running KVM. On the other hand, any other number means you can proceed with the installation.

2. When the installation completes, rerun the command to check KVM acceleration availability, and if everything is ok, you are ready to start installing KVM.

Step 3: Install KVM Packages
-
Install the essential KVM packages with the following command:

sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils -y

Step 4: Authorize Users
-
Only members of the libvirt and kvm user groups can run virtual machines. If you want specific users to run VMs, add them to those user groups. Follow the steps below:

1. Add the user you want to run the virtual machines to the libvirt group:

sudo adduser [username] libvirt

2. Next, do the same for the kvm group:

sudo gpasswd -a [username] libvirt

sudo gpasswd -a [username] kvm

Step 5: Verify the Installation
-
Confirm that the KVM installation was successful with the virsh command. The virsh command is a command-line tool for managing virtual machines on Linux systems. Run the command below:

sudo virsh list --all

Alternatively, use the systemctl command to check the status of libvirtd, the daemon that provides the backend services for the libvirt virtualization management system:

sudo systemctl status libvirtd

If the virtualization daemon is not active, activate it with the following command:

sudo systemctl enable --now libvirtd
