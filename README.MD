INSTALL:
-
- https://ubuntu.com/blog/kvm-hyphervisor
- https://wiki.sharewiz.net/doku.php?id=kvm:list_os_variants
- https://phoenixnap.com/kb/ubuntu-install-kvm

DOCS:
-
- https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-guest_virtual_machine_installation_overview-creating_guests_with_virt_install#sect-Guest_virtual_machine_installation_overview-Creating_guests_with_virt_install

LAUNCH:
-
- https://docs.fedoraproject.org/en-US/fedora-server/virtualization/vm-install-diskimg-fedoraserver/
- https://infotechys.com/create-a-virtual-machine-in-kvm-using-virt-install/

COMMAND:
-
- cp /var/lib/libvirt/boot/Fedora-Server-KVM-40-1.14.x86_64.qcow2 /var/lib/libvirt/images/fedora40.qcow2

- virt-install \
--name fedora40 \
--os-variant fedora40 \
--memory 4096 \
--cpu host --vcpus 4 \
--import \
--disk /var/lib/libvirt/images/fedora40.qcow2,format=qcow2,bus=virtio \
--network network=default \
--graphics none \
--console pty,target_type=serial

VIRSH CHEATSHEET:
-
- virsh list --all  - list all vm's
- virsh define <file>  - create vm
- virsh undefine VM1  - delete vm
- virsh start VM1  - start created vm
- virsh destroy VM1  - stop vm
- virsh dominfo VM1  - vm info
- virsh setmaxmem VM1 80M  - change stopped vm max ram
- virsh autostart VM1

TO DELETE VM (DOMAIN):
- virsh destroy VM1
- virsh undefine VM1

TO CONNECT:
- virsh console VM1
