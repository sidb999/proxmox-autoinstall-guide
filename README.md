<!-- markdownlint-disable MD010 -->
<!-- markdownlint-disable MD013 -->
<!-- markdownlint-disable MD018 -->
<!-- markdownlint-disable MD034 -->
<!-- markdownlint-disable MD033 -->

# Creating the autoinstall proxmox image guide

[OFFICIAL GUIDE](https://pve.proxmox.com/wiki/Automated_Installation)

## Downloading prerequisites

- download the latest versions of ISO and autoinstall assistant:
  - [ISO](https://www.proxmox.com/en/downloads)
  - [proxmox-auto-install-assistant](http://download.proxmox.com/debian/pve/dists/bookworm/pve-no-subscription/binary-amd64/)

## Configure the answer.toml config

```bash
cp example.toml answer.toml
# edit the answer.toml
# Change the target disk to setup fx. `/dev/sda`,
#   fill your country, email, etc
#   (!) and ADD YOUR PUBLIC SSH KEY.
```

## Install the prerequisites

### Debian

```bash
sudo dpkg -i proxmox-auto-install-assistant*.deb
```

### Archlinux

```bash
# install debtap for being able to install the debian packages in archlinux
yay -S --needed debtap
# update the debtap repos
sudo debtap -u

# enter the result name for the system package
# skip the other options
debtap proxmox-auto-install-assistant*.deb

# zst archive is the output of the previous command
# it contains the usual arch package
sudo pacman -U proxmox-auto-install-assistant*.zst
```

## Create the image with autoinstall boot option and embedded answer file

```bash
# Validate you answer file
# Build the autoinstall proxmox image
proxmox-auto-install-assistant validate-answer answer.toml && \
proxmox-auto-install-assistant prepare-iso proxmox-ve_8.3-1.iso --fetch-from iso --answer-file answer.toml
```
