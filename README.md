# Proxmox All-in-One NAS + Jellyfin LXC Server

This project guide provides the steps to create a single, efficient Proxmox LXC container that serves as both a **Samba File Share (NAS)** and a **Jellyfin Media Server**.

This all-in-one approach is lightweight and avoids all the network mounting and permission issues that come from running them in separate containers.



## Prerequisites

* A running Proxmox VE host.
* Storage on your Proxmox host (e.g., `local-lvm`).
* A Debian 12 (or similar) LXC template.

## Project Steps

Follow these guides in order to build your server.

1.  [**Create the LXC Container**](./01-create-lxc.md)
2.  [**Install and Configure Samba**](./02-configure-samba.md)
3.  [**Install and Configure Jellyfin**](./03-install-jellyfin.md)
4.  [**Configure Container Resources**](./04-configure-resources.md)
5.  [**Final Setup and Usage**](./05-final-setup.md)
