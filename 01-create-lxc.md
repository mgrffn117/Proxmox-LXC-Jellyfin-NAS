# Step 1: Create the LXC Container

First, we create the container and, most importantly, attach a large dedicated virtual disk for media storage.

1.  **On your Proxmox Host**, update your templates:
    ```bash
    pveam update
    ```

2.  Find the Debian 12 template (or a similar base like Ubuntu):
    ```bash
    pveam available --section system | grep debian-12-standard
    ```

3.  Download the template:
    ```bash
    pveam download local debian-12-standard.tar.zst
    ```

4.  Create the container. You can use these variables or fill in your own values.
    ```bash
    # Set your variables
    CT_ID="105"
    CT_HOSTNAME="media-server"
    CT_BRIDGE="vmbr0"
    CT_PASS="YourSecurePassword"
    CT_TEMPLATE="local:vztmpl/debian-12-standard.tar.zst"
    CT_STORAGE_POOL="local-lvm"

    # Create the container
    pct create $CT_ID $CT_TEMPLATE \
        --hostname $CT_HOSTNAME \
        --password $CT_PASS \
        --net0 name=eth0,bridge=$CT_BRIDGE,ip=dhcp \
        --onboot 1
    ```

5.  **Add the Media Storage Disk.** This is the key. We will add a 4TB (4096GB) disk.
    ```bash
    # Syntax: pct set [ID] -mp0 [STORAGE_POOL]:[SIZE_GB],mp=[MOUNT_PATH]
    pct set $CT_ID -mp0 $CT_STORAGE_POOL:4096,mp=/mnt/share
    ```
    *This creates a 4TB virtual disk and mounts it at `/mnt/share` inside the container.*

6.  Start your new container:
    ```bash
    pct start $CT_ID
    ```

---
**Next Step:** [**Step 2: Install and Configure Samba**](./02-configure-samba.md)
