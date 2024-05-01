Proxmox Backup Guide
====================

Description
-----------

This document describes how to perform backups and restore virtual machines (VMs) and LXC containers on Proxmox VE.

Requirements
------------

*   A server with Proxmox VE installed
*   Access to the Proxmox administrative panel
*   Configured storage for backups (local, NFS, or other)

How to Perform a Backup
-----------------------

### Virtual Machine (VM) Backup

1.  Log in to the Proxmox VE panel.
2.  Select the appropriate server (node) and VM from the list on the left side.
3.  Go to the `Backup` tab.
4.  Click `Backup now`.
5.  Choose the backup storage, backup format, and type of operation (e.g., live backup).
6.  Click `Backup` to start the process.

### LXC Container Backup

1.  Log in to the Proxmox VE panel.
2.  Select the appropriate server (node) and LXC container from the list on the left side.
3.  Go to the `Backup` tab.
4.  Click `Backup now`.
5.  Choose the backup storage and other configuration options.
6.  Click `Backup` to start the process.

How to Restore from Backup
--------------------------

1.  Log in to the Proxmox VE panel.
2.  Go to the `Storage` tab and select the storage where backups are kept.
3.  Find the relevant backup and choose the `Restore` option.
4.  Follow the on-screen instructions to restore the VM or LXC container.

Backup File Location
--------------------

*   Default location for local backups: `/var/lib/vz/dump/`
*   For NFS/CIFS storages, the location depends on the storage configuration.
*   Check the storage configuration under `Datacenter -> Storage` in the Proxmox panel.

Scheduling Automatic Backups
----------------------------

1.  Go to `Datacenter -> Backup`.
2.  Create a new backup job (`Add`).
3.  Configure the schedule, select VMs/containers for backup, storage, and other options.
4.  Save the configuration.
