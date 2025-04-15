| Author      | Created on  | Version    | Last updated by | Last edited on |
|-------------|-------------|------------|-----------------|----------------|
| Aditya Tripathi   | 14-04-25    | version 2  | Aditya Tripathi        | 15-04-25       |


# Ubuntu Installation and Concepts Documentation

This document provides a comprehensive guide to installing and managing Ubuntu, focusing on version 22.04 (Jammy Jellyfish). It covers essential concepts, best practices, and common operations.

## Table of Contents

1.  [Ubuntu History](#ubuntu-history)
2.  [Why Ubuntu?](#why-ubuntu)
3.  [What is Ubuntu?](#what-is-ubuntu)
4.  [Software Management and Services](#software-management-and-services)
5.  [Ubuntu 22.04 Stable Version](#ubuntu-2204-stable-version)
6.  [Installation Guide (Ubuntu 22.04)](#installation-guide-ubuntu-2204)
    * [Pre-Checks](#pre-checks)
    * [Installation Steps](#installation-steps)
    * [Post-Checks](#post-checks)
7.  [Software Installation and Updates](#software-installation-and-updates)
    * [Update vs. Upgrade](#update-vs-upgrade)
    * [Package Management](#package-management)
    * [When and Which Packages to Install](#when-and-which-packages-to-install)
    * [Purpose of Update and Upgrade](#purpose-of-update-and-upgrade)
    * [Offline Installation](#offline-installation)
    * [Binary Installation](#binary-installation)
8.  [Service Management in Ubuntu](#service-management-in-ubuntu)
    * [Systemd (etc/systemd)](#systemd-etcsystemd)
9.  [Configuration Files in /etc](#configuration-files-in-etc)
10. [Common Operations in Ubuntu](#common-operations-in-ubuntu)

## Ubuntu History

Ubuntu is a Debian-based Linux distribution developed by Canonical. Its first release was in October 2004. It was designed to be a user-friendly and accessible operating system. The name "Ubuntu" comes from a Zulu word meaning "humanity to others." Mark Shuttleworth, the founder of Canonical, aimed to create a Linux distribution that was easy for everyone to use.

## Why Ubuntu?

* **User-Friendly:** Known for its ease of use and intuitive interface.
* **Open Source:** Free and open-source, promoting community development.
* **Stability:** Regular releases and long-term support (LTS) versions provide stability.
* **Large Community:** Extensive community support and documentation.
* **Software Availability:** Vast software repository and package management system.

## What is Ubuntu?

Ubuntu is a complete Linux-based operating system, primarily aimed at desktop users, but also used on servers and cloud platforms. It's built on the Debian architecture and uses the `apt` package management system.

## Software Management and Services

Ubuntu's software management is robust, offering tools to install, update, and remove applications. Services are managed through `systemd`, providing a standardized way to control background processes.

## Ubuntu 22.04 Stable Version

Ubuntu 22.04 (Jammy Jellyfish) is a Long Term Support (LTS) release, providing five years of support until April 2027. It includes an updated kernel, GNOME desktop environment, and improved performance.

## Installation Guide (Ubuntu 22.04)

### Pre-Checks

* **System Requirements:** Ensure your system meets the minimum requirements.
* **Backup Data:** Back up important files before installation.
* **Download ISO:** Download the Ubuntu 22.04 ISO from the official Ubuntu website.
* **Create Bootable Media:** Create a bootable USB drive or DVD.
* **BIOS/UEFI Settings:** Configure BIOS/UEFI to boot from the installation media.

### Installation Steps

1.  Boot from the installation media.
2.  Select "Install Ubuntu."
3.  Choose language and keyboard layout.
4.  Select installation type (Normal or Minimal).
5.  Choose partitioning method (Erase disk or Something else).
6.  Create user account and set password.
7.  Wait for installation to complete.
8.  Restart the system.

### Post-Checks

* **Update System:** Run `sudo apt update && sudo apt upgrade`.
* **Install Drivers:** Install necessary drivers (e.g., graphics drivers).
* **Configure Network:** Configure network settings if needed.
* **Install Essential Software:** Install essential applications.

## Software Installation and Updates

### Update vs. Upgrade

| Feature        | `apt update`                                   | `apt upgrade`                                        |
| :------------- | :--------------------------------------------- | :--------------------------------------------------- |
| Purpose        | Updates package lists                           | Installs newer versions of packages                  |
| Action         | Fetches package information from repositories  | Downloads and installs updates                       |
| Changes        | Updates package lists, but does not install new software | Installs new versions of *existing* packages.      |

### Package Management

Ubuntu uses the `apt` (Advanced Package Tool) package management system.

### When and Which Packages to Install

* **New Software:** Use `sudo apt install <package_name>` to install new software.
* **Essential Packages:** `build-essential`, `git`, `vim`, `curl`, `wget`.
* **Specific Needs:** Install packages based on your requirements (e.g., development tools, media players).

### Purpose of Update and Upgrade

* **`apt update`:** Ensures you have the latest package information from the repositories.  It updates the list of available packages and their versions.
* **`apt upgrade`:** Installs the newest versions of *all* packages currently installed on the system, but only if those new versions don't require installing any new packages.

### Offline Installation

Offline installation involves downloading packages on a system with internet access and then installing them on an offline system.

1.  **Download Packages:** Use `apt download <package_name>` on a system with internet.
2.  **Transfer Packages:** Transfer the downloaded `.deb` files to the offline system.
3.  **Install Packages:** Use `sudo dpkg -i <package_name>.deb` to install the packages.
    * If there are dependency errors, you may need to download the dependent packages as well and install them.
4.  **Fix Dependencies (If necessary):** After transferring and installing, if you encounter dependency issues, use `sudo apt install --fix-broken`.  This command attempts to resolve unmet dependencies.  However, this command requires access to the repositories defined in your system's configuration, and in a truly offline situation, it will not work.  You would need to manually download all dependencies.

### Binary Installation

Binary installation involves downloading and installing pre-compiled software packages. These are not managed by `apt` and require manual installation and dependency management.  Often, you download a `.tar.gz`, `.tar.bz2`, or similar archive, extract it, and then run a configuration and/or installation script (if provided).  Sometimes it involves just copying the extracted files to a specific location.

## Service Management in Ubuntu

### Systemd (etc/systemd)

`systemd` is the system and service manager for Linux. It manages system services and processes. Configuration files are located in `/etc/systemd/`.

* **`systemctl start <service_name>`:** Start a service.
* **`systemctl stop <service_name>`:** Stop a service.
* **`systemctl restart <service_name>`:** Restart a service.
* **`systemctl status <service_name>`:** Check service status.
* **`systemctl enable <service_name>`:** Enable a service to start on boot.
* **`systemctl disable <service_name>`:** Disable a service from starting on boot.

## Configuration Files in /etc

The `/etc` directory contains system-wide configuration files. These files control various aspects of the operating system, including networking, services, and user settings.  Examples include `/etc/network/interfaces` (though now often superseded by `netplan`), `/etc/resolv.conf`, and `/etc/ssh/sshd_config`.

## Common Operations in Ubuntu

* **Update System:** `sudo apt update && sudo apt upgrade`
* **Install Software:** `sudo apt install <package_name>`
* **Remove Software:** `sudo apt remove <package_name>` or `sudo apt purge <package_name>` (to also remove configuration files)
* **List Installed Packages:** `dpkg -l`
* **Search for Packages:** `apt search <keyword>`
* **Show Package Information: `apt show <package_name>`
* **Check Disk Space:** `df -h`
* **Check Memory Usage:** `free -m`
* **View System Logs:** `journalctl` (or `/var/log/syslog`, `/var/log/auth.log`, etc.)
* **Network Configuration:** `ip addr`, `ifconfig` (may need to install `net-tools`), `netplan`
* **File Permissions:** `chmod`, `chown`
* **Text Editing:** `nano`, `vim`


## Contact Information
| Name         | Email address          |
|--------------|------------------------|
| Aditya Tripathi          | aditya.tripathi.snaatak@mygurukulam.co     |

## Reference Links
| Links        | Descriptions         |
|--------------|------------------------|
|    https://shorturl.at/Uhogh | Explore the technical reasons behind my preference for Ubuntu, focusing on its efficiency, compatibility with development tools, and cost-effectiveness. |
https://shorturl.at/0WUPt     |   A detailed documentation on systemd.   |
