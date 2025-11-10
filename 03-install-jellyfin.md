# Step 3: Install and Configure Jellyfin

Inside the *same container*, we will now install Jellyfin and grant it access to the media.

1.  Install `curl` (if it's not already installed), which is needed for the script:
    ```bash
    apt install curl -y
    ```

2.  Run the official Jellyfin install script. This adds their repository and installs the server:
    ```bash
    curl -s [https://repo.jellyfin.org/install-debuntu.sh](https://repo.jellyfin.org/install-debuntu.sh) | sudo bash
    ```

3.  **Configure Permissions:**
    Jellyfin runs as its own user (`jellyfin`) and needs permission to read the files in `/mnt/share` (which will be owned by `root` from your Samba transfers).

    The simplest way to grant access is to add the `jellyfin` user to the `root` group.

    ```bash
    usermod -aG root jellyfin
    ```

4.  Restart Jellyfin to pick up its new group membership:
    ```bash
    systemctl restart jellyfin
    ```

---
**Next Step:** [**Step 4: Configure Container Resources**](./04-configure-resources.md)
