
# Docker ext4.vhdx Optimization Guide

If you're using Docker on WSL 2 and notice that the `ext4.vhdx` file is taking up a lot of space, you can optimize it to reduce its size. Follow these steps to compact the `ext4.vhdx` file using Command Prompt (CMD) or PowerShell.

## Prerequisites

- Docker for Windows with WSL 2 backend enabled

## Steps

1. **Shutdown WSL:**

   Open Command Prompt or PowerShell and run this command to shut down WSL:

   ```shell
   wsl --shutdown
   ```

2. **List WSL Distros:**

   Run this command to list WSL distributions and their details:

   ```shell
   wsl.exe --list --verbose
   ```

3. **Open DiskPart:**

   Launch DiskPart utility by entering this command in CMD or PowerShell:

   ```shell
   diskpart
   ```

4. **Compact ext4.vhdx:**

   Within the DiskPart environment, use these commands to select and compact the `ext4.vhdx` file:

   ```shell
   select vdisk file="C:\Users\username\AppData\Local\Docker\wsl\data\ext4.vhdx"
   compact vdisk
   ```

   You'll see progress feedback, and once the process is completed, you'll get a success message:

   ```shell
   DISKPART> compact vdisk
     100 percent completed
   DiskPart successfully compacted the virtual disk file.
   ```

