# Linux Hardware Communication — Deep Dive
🔑 The kernel is the brain — it sits between hardware and applications. It never lets user programs talk directly to hardware. Everything goes through the kernel.

## How Linux Communicates with Hardware (Overview)
When you power on a Linux machine, there is a chain of communication:
```mermaid
flowchart TD
    A["Hardware (CPU, RAM, GPU, Disk, NIC)"]
    B["Firmware (BIOS / UEFI)"]
    C["Linux Kernel"]
    D["Kernel Subsystems (drivers, buses)"]
    E["Device Files (/dev/sda, /dev/nvidia0)"]
    F["User Space Applications"]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F

---

Linux uses drivers (kernel modules) to talk to hardware via PCIe/USB buses
lshw, dmidecode, lspci are tools that query hardware info from different sources
Most Linux drivers are GPL open source and live inside the kernel tree
Proprietary drivers can't be merged into the kernel due to GPL licensing
NVIDIA has historically been the most notorious for proprietary drivers — but since 2022, they released nvidia-open kernel modules
nvtop is an excellent real-time GPU monitoring tool for NVIDIA, AMD, and Intel GPUs