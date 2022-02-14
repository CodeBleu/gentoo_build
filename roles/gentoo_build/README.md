gentoo_build
=========

Role to setup Gentoo with full encryption & EFI

Requirements
------------

### setup wifi

`/etc/wpa_supplicant/wpa_supplicant.conf`


    network={
        ssid="<ssid>"
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="<password>"
    }

### Wipe all partitions on dest

make sure you remove all partitions on drive so role with create the primary partition correctly

### set password for root

livecd ~#: `passwd`

### enable ssh server

`/etc/ssh/sshd_config`

**uncomment the following**

    Port 22`
    ListenAddress 0.0.0.0`

### ensure gpg key is in location in defaults file


    livecd_usb_luks_key: <path>


### Copy ssh key to ansible

    ssh-copy-id root@<ip of livecd>

### Create inventory file for ansible

`~/inventory`

    livecd ansible_host=<ip> ansible_user=root ansible_ssh_pipelining=False


Role Variables
--------------

See  ../defaults/main.yml


Dependencies
------------

* passwordstore password tool
* gpg key already created for LUKS

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
      become: true
         - { role: gentoo_build }

License
-------

BSD-3

Author Information
------------------

Jason Hollis
