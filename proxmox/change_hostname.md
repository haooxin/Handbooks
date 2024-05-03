# Renaming a PVE node


Proxmox VE uses the hostname as a nodes name, so changing it works similar to changing the host name. This must be done on a empty node.

## Change Hostname
Rename a standalone PVE host, you need to edit the following files:

/etc/hosts
/etc/hostname
You can use pre-installed editor like nano (easy) or vi (advanced), for example:

nano /etc/hosts
In the above files replace all occurrences of the old name with the new one. Ensure that /etc/hosts has an entry with the hostname mapped to the IP you want to use as main IP address for this node.

There are other files which you may want to edit, they are not important for the functions of Proxmox VE itself.

/etc/mailname
/etc/postfix/main.cf
If your node is in a cluster, where it is not recommended changing its name, adapt /etc/pve/corosync.conf so that the nodes name is changed also there. See https://pve.proxmox.com/pve-docs/chapter-pvecm.html#pvecm_edit_corosync_conf

## Cleanup
The SSH keys don't need to be edited unless you really want to (and if you do, make sure you make the corresponding change on every other machine that SSH public key appears on).

Now move the configuration files, as the pmxcfs has a few restrictions to ensure consistency you cannot rename non empty folders. Thus if you have VMs or Containers on the node, which is not recommended when changing a nodes name, you have to recreate the folder structure and copy files per folder level.

Also copy the contents of ***/var/lib/rrdcached/db/pve2-{node,storage}/old-hostname*** to ***/var/lib/rrdcached/db/pve2-{node,storage}/new-hostname*** and remove the old directory.

Alternatively, make a backup of the VMs and LXC containers, clean up the node and restore the copy to a node with a new name.
