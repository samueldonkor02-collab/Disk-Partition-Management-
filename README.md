# Disk-Partition-Management-
Reviewed a Windows 11 disk's full partition layout in Disk Management, identifying hidden system partitions (EFI, recovery) alongside the OS drive and connecting each to its role in boot/recovery.

# Disk Partition Review (Volume Layout via Disk Management)

`Windows 11` `Disk Management` `This PC` `Partitions` `Volumes`

## Overview
This section covers using Disk Management and This PC to examine the full partition layout of a Windows 11 machine, including hidden system partitions that don't normally show up with a drive letter in File Explorer.

## Objective
Get comfortable reading a complete disk/volume layout in Disk Management rather than just the handful of lettered drives visible in everyday use, and understand what each partition on the disk is actually for.

## Environment
* Machine: Windows 11 desktop
* Tools used: Disk Management (diskmgmt.msc), File Explorer / This PC
* Disk: Disk 0, Basic, 476.92 GB, Online

## What I Did

### Opening Disk Management
Launched Disk Management and looked at the volume list for Disk 0. Beyond the OS (C:) drive that shows up normally in File Explorer, there were three unlettered system partitions: a 260 MB EFI system partition, a 991 MB partition, and a second 260 MB recovery partition, all listed as Healthy with no drive letter assigned. None of these are meant to be browsed directly, they exist to support boot and recovery.

### Reading the Graphical View
The lower pane in Disk Management showed the same partitions laid out visually across the physical disk, color-coded and sized roughly proportional to their actual space. This made it easier to see how a single physical disk gets carved up: a small EFI boot partition, the large OS (C:) partition taking up most of the disk (465.45 GB), and a recovery partition tucked at the end.

### Cross-Checking in This PC
Switched to This PC to see the same disk from the everyday user view, which only exposes OS (C:) with 369 GB free of 465 GB. The hidden system partitions, the two DVD drives, and the external "my back up" (F:) drive were also visible there, but without any of the layout or partition-type detail that Disk Management provides.

### Thinking Through the Layout
Seeing the full partition table made it clear why File Explorer hides certain partitions by default, they're not meant for casual browsing and don't contain user files, but they're essential to how the disk boots and recovers. It also reinforced how "one drive" from a user's perspective (C:) is really just one partition among several on the physical disk.

## What's in This Section

```
screenshots/
01 disk management volume list.png (Disk Management showing all partitions on Disk 0, including hidden system partitions)
02 this pc drives view.png (This PC, showing only the user-facing drives and free space)
```

## Skills I Picked Up
Reading a full Disk Management partition table, including unlettered system partitions.
Understanding the difference between what File Explorer exposes to users versus the actual physical disk layout.
Connecting partition type (EFI, recovery, primary) to its functional role in booting and recovering Windows.

## How This Applies in the Real World
Being able to read a partition table matters for tasks like troubleshooting boot issues, preparing a disk for encryption or imaging, or investigating a machine during incident response, where knowing what's actually on the disk (not just what's shown by default) is often the first step.

## Limitations
This was a GUI-level walkthrough, not a forensic-level disk analysis. It doesn't cover partition GUIDs, sector-level detail, or anything beyond what Disk Management's standard view exposes.

## References
Disk Management Documentation: https://learn.microsoft.com/windows-server/storage/disk-management/overview-of-disk-management
Windows Partition Types Overview: https://learn.microsoft.com/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions
