# Step 5: Final Setup and Usage

You are all done! The container is running with both services.

1.  **Access your Samba Share:**
    * From a file explorer (like on Windows), navigate to `\\[CONTAINER_IP]\public`
    * When prompted, use the username `root` and the password you set with `smbpasswd`.
    * Drag and drop your movies, TV shows, and music into this folder.

2.  **Access your Jellyfin Server:**
    * Open your web browser and go to `http://[CONTAINER_IP]:8096`
    * Follow the first-time setup wizard.

3.  **Add Media to Jellyfin:**
    * When the wizard asks you to "Add Media Library," select your content type (e.g., "Movies").
    * For the **Folder**, just use the local path: `/mnt/share`
    * Add your other libraries (e.g., "TV Shows") and point them to the same `/mnt/share` path.

Jellyfin will now scan the files you added via Samba and make them available for streaming.

---
**Project Complete!** [**Return to main README**](./README.md)
