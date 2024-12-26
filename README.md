<!-- markdownlint-disable MD010 -->
<!-- markdownlint-disable MD013 -->
<!-- markdownlint-disable MD018 -->
<!-- markdownlint-disable MD034 -->
<!-- markdownlint-disable MD033 -->

# Creating the autoinstall proxmox image guide

[OFFICIAL GUIDE](https://pve.proxmox.com/wiki/Automated_Installation)

## Download Proxmox iso

- [ISO downloads page](https://www.proxmox.com/en/downloads)

## Download autoinstall shit

- [proxmox-auto-install-assistant_8.3.4_amd64.deb](http://download.proxmox.com/debian/pve/dists/bookworm/pve-no-subscription/binary-amd64/)

## Lets get our hands dirty

```bash
sudo debtap -u
debtap proxmox-auto-install-assistant_8.3.4_amd64.deb
sudo pacman -U proxmox-auto-install-assistant-8.3.4-1-x86_64.pkg.tar.zst
proxmox-auto-install-assistant validate-answer answer.toml
proxmox-auto-install-assistant prepare-iso proxmox-ve_8.3-1.iso --fetch-from iso --answer-file answer.toml
```
