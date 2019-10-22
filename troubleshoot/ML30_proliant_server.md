# ML30 Proliant Gen10

## Enabling embedded chipset SATA controller support

```
Problem : Even after installing the OS on the servers, they did not boot into them. Ensuring the priority even didn't help. 

```

Our cloud comprises of 10 of ML30 Gen10 servers over which we are running RHEL7/CentOS7 operating systems. Out of the box the disks are configured to be in RAID configuration but the disks are not assigned to the RAID. Since, we are not using RAID for our servers, we had to enable the **AHCI** support for it. Below is a crude process to get the servers to run AHCI.

##### Prerequisites
 - The correct operating system drivers for your selected option.
 - Boot Mode is set to UEFI Mode.
##### Procedure
1. From the **System Utilities** screen, select **System Configuration > BIOS/Platform Configuration (RBSU) > System Options > SATA Controller Options > Embedded SATA Configuration** and press **Enter**.
2. Ensure that you are using the correct ACHI or RAID system drivers for your SATA option.
3 .Select a setting and press **Enter**.
  - **Enable SATA AHCI Support** — Enables the embedded chipset SATA controller for AHCI.
4. Press **F10**.