# Step 4: Configure Container Resources

This container is now running two services (Samba + Jellyfin). The default 512MB of RAM is not enough. We need to increase it.

1.  **On the Proxmox Host** (not inside the container), stop the container:
    ```bash
    # Replace 105 with your CT_ID
    pct stop 105
    ```

2.  Set the memory to 2GB (2048MB) and add 1GB of swap. This can also be done from the container's "Resources" tab in the Proxmox UI.
    ```bash
    pct set 105 --memory 2048 --swap 1024
    ```

3.  Start the container:
    ```bash
    pct start 105
    ```

---
**Next Step:** [**Step 5: Final Setup and Usage**](./05-final-setup.md)
