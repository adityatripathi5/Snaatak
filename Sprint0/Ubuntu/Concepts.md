#  Ubuntu Operating System - Installation & Concepts

Welcome to the comprehensive guide for understanding Ubuntu Linux, focusing on installation, software management, and service handling in **Ubuntu 22.04 LTS**. This documentation is beginner-friendly and aims to provide a foundational understanding of working with Ubuntu systems.

---

##  What is Ubuntu?

Ubuntu is a **free and open-source** Linux distribution based on **Debian**. It's user-friendly, secure, and widely used for desktops, servers, and cloud systems. Ubuntu is developed and maintained by **Canonical Ltd.**

---

##  Brief History

- **Released:** First version in 2004
- **Name Meaning:** "Ubuntu" is an African term meaning *"humanity to others"*
- **LTS Releases:** Ubuntu has **Long-Term Support (LTS)** releases every two years with five years of security updates.

---

##  Why Ubuntu?

- User-friendly interface (especially with GNOME)
- Wide community support
- Regular LTS versions for stability
- Default OS for many cloud providers
- Great for developers and sysadmins

---

##  Ubuntu 22.04 LTS (Jammy Jellyfish)

- **Release Date:** April 2022
- **Support Until:** April 2027
- **Kernel Version:** Linux 5.15
- **Features:** GNOME 42, improved performance, security updates

---

##  Pre-Checks Before Installation

- Minimum 4GB RAM & 25GB storage
- UEFI/BIOS boot mode awareness
- Backup existing data
- Create bootable USB (Rufus, Balena Etcher)

---

##  Installation Steps (Ubuntu 22.04)

1. Boot from USB
2. Choose *Try Ubuntu* or *Install Ubuntu*
3. Select language, keyboard layout
4. Choose installation type (Normal/Minimal)
5. Allocate disk space (Manual/Automatic)
6. Set up user credentials
7. Complete installation and reboot

---

##  Post-Installation Checklist

- Connect to Internet and check ports.
- Run software updates
- Enable firewall (ufw)
- Install essential packages (`git`, `curl`, `build-essential`)
- Configure time zone and locale

---

##  Software Installation & Update

### Install New Software

sudo apt install <package-name>

### Update Existing Software

sudo apt update

### Upgrade Software

sudo apt upgrade

---

## Difference: update vs upgrade

### Command	### Purpose
apt update	Refreshes the local package index
apt upgrade	Installs the newest versions of all packages

---

## Package Management
Ubuntu uses APT (Advanced Package Tool) for managing packages.

Install: sudo apt install package

Remove: sudo apt remove package

Search: apt search package

List: apt list --installed

Tip: Always check the purpose of a package before installing it!

---

## Offline Installation
Use apt download <package> on another internet-enabled machine

Transfer .deb file via USB

Install using sudo dpkg -i <package>.deb

Use apt-offline for full dependency support

---

## Managing Services in Ubuntu
Ubuntu uses systemd to manage services.

## Common Commands:

# Start a service
sudo systemctl start nginx

# Enable on boot
sudo systemctl enable nginx

# Check status
sudo systemctl status nginx

---

## Binary Installation
Used when:

Software is not available in repositories

You need a specific version

---

## Steps:

Download the binary

Make it executable: chmod +x

Move to /usr/local/bin/

---

Configuration Files in /etc
Location for system-wide configuration files

## Examples:

/etc/hostname

/etc/network/interfaces

/etc/fstab

---

## Modify with care using sudo.

systemd & /etc/systemd
systemd is the default init system

Units are defined in /etc/systemd/system/

Each .service file describes how a service starts, stops, and restarts

---

## Software Management Summary
Use apt for easy management

Keep system updated for security

Prefer LTS versions of software

Understand when to use binary or repo-based install

---

## Common Ubuntu Operations

## Task	 ## Command
Update System	sudo apt update && sudo apt upgrade
Add User	sudo adduser username
Change Hostname	sudo hostnamectl set-hostname new
Enable Firewall	sudo ufw enable
Check Disk Usage	df -h
Monitor System	htop / top
Reboot	sudo reboot

---

## Resources
Official Ubuntu Docs

Ubuntu Wiki

AskUbuntu

---

## Tip: Always read the man pages: man <command> for more information.

## Contributions
Feel free to fork this repo and contribute via pull requests to make this guide even better!
