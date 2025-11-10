# Step 2: Install and Configure Samba

Now, we enter the container and set up the file share.

1.  Enter the container's shell (using the ID you set, e.g., `105`):
    ```bash
    pct enter 105
    ```

2.  Install Samba (inside the container):
    ```bash
    apt update
    apt install samba -y
    ```

3.  Set a Samba password for the `root` user. This will be your login from Windows/Mac.
    ```bash
    smbpasswd -a root
    ```

4.  Configure the share. Open `/etc/samba/smb.conf` with `nano`:
    ```bash
    nano /etc/samba/smb.conf
    ```

5.  Scroll to the very bottom and add this block. This tells Samba to share the `/mnt/share` directory and that the `root` user is allowed to access it.
    ```ini
    [public]
       comment = Public Share
       path = /mnt/share
       browseable = yes
       writeable = yes
       valid users = root
       create mask = 0777
       directory mask = 0777
    ```

6.  Save the file (`CTRL+O`, `Enter`) and exit (`CTRL+X`).

7.  Restart Samba to apply the changes:
    ```bash
    systemctl restart smbd
    ```

> **Your file share is now active!** You can test it by connecting from another computer at `\\[CONTAINER_IP]\public`.

---
**Next Step:** [**Step 3: Install and Configure Jellyfin**](./03-install-jellyfin.md)
