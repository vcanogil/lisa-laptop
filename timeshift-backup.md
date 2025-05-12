
# 🖥️ Getting Started with Timeshift (GUI)

Timeshift is an application to backup and restore your system.

I made a backup partition on your laptop where the backups will be stored (sda3, label "backup")

Don't backup your personal files, you don't have the space. 

---

## 🧭 Main Interface Overview

After entering your password, you'll see the Timeshift main window. It contains a **toolbar** at the top and an **empty list** (until you create your first snapshot).

Here’s what the main buttons do:

| Button      | What it Does                                                                 |
|-------------|-------------------------------------------------------------------------------|
| **Create**  | Take a snapshot of your system as it is right now                            |
| **Restore** | Revert your system to a previous snapshot                                    |
| **Delete**  | Remove a selected snapshot to free up space                                  |
| **Browse**  | Open the selected snapshot in your file browser to look inside it            |
| **Settings**| Configure snapshot location, schedule, and which files or users to include   |
| **Wizard**  | Reopen the initial setup wizard if you want to reconfigure everything        |

---

## 📸 Creating Your First Snapshot

Click **Create** to take a manual snapshot. Timeshift will:
- Save the state of your system files
- Store the snapshot in your selected location (default: your root partition, unless changed)

After it’s done, the snapshot will appear in the list with the date, size, and description.

---

## 🔄 Restoring a Snapshot

To undo changes or fix a broken system:
1. Select a snapshot from the list
2. Click **Restore**
3. Follow the guided steps and reboot

**Warning:** This replaces system files. It won’t affect your personal files (unless you explicitly included them in settings).

---

## 🗑️ Deleting Snapshots

Click **Delete** on any old snapshot to free up disk space. Timeshift handles this safely — it won't let you delete all backups if you're relying on them.

---

## 🧪 Browsing Snapshots

Want to peek inside a backup?
- Click **Browse** to open the snapshot in a file manager.
- You can copy files out manually if needed — like restoring just one config file.

---

## ⚙️ Settings You Should Check

Click **Settings** and review:
- **Location:** Where to store snapshots (e.g., external drive)
- **Schedule:** Daily/weekly/monthly automatic snapshots
- **Users:** Whether to include your personal files (`/home`) — disabled by default
- **Filters:** What files or folders to include/exclude


# 🛠️ Restoring Timeshift Snapshot When You Can’t Boot Into Linux

If your Linux system becomes unbootable, you can still restore it using a **Live USB** and your Timeshift backups. Here's a step-by-step guide.

---

## 🧰 What You Need

- A second computer (temporarily) to create a bootable USB
- A USB drive (4 GB or larger)
- A Lubuntu ISO file (get it from https://lubuntu.me/downloads/)
- Your Timeshift backup must be saved to another partition or external drive

---

## 🔥 Step 1: Create a Bootable Lubuntu USB

### On a Linux system:
1. Plug in your USB drive.
2. Open the **Startup Disk Creator** (usually installed by default).
3. Select the **Lubuntu ISO** and your USB device.
4. Click **"Make Startup Disk"**.

### On Windows (alternative tools):
- Use **Rufus** or **balenaEtcher**.

---

## 🚀 Step 2: Boot from the Live USB

1. Insert the USB into the broken system.
2. Power on the computer and press the key for **Boot Menu** (`F12`, `Esc`, or `Del` — depends on your machine).
3. Select the USB device.
4. Choose **“Try Lubuntu without installing.”**

---

## 💽 Step 3: Mount Your Backup Partition

1. Open the **file manager** from the Lubuntu desktop.
2. Locate and open the partition where your **Timeshift snapshots** are stored.
3. Leave that file manager window open (this will auto-mount the disk).

---

## 🧭 Step 4: Install Timeshift in the Live Session

Open a terminal:
```bash
sudo apt update
sudo apt install timeshift
```

---

## 🔄 Step 5: Restore the Snapshot

1. Launch Timeshift from the app menu or terminal:
```bash
sudo timeshift-gtk
```
2. In the Timeshift GUI:
   - Select the snapshot from your backup partition.
   - Click **Restore**.
   - Follow the prompts to overwrite system files.

3. When it’s done, reboot your system:
```bash
sudo reboot
```

---

## ✅ Done

Your system should now be restored to the snapshot you selected. Make sure to take a new backup once things are stable again.

---
