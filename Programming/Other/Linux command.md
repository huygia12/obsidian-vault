---
created: 1970-01-01T08:00
updated: 2024-05-07T09:41
tags:
  - Linux
---
## System:
- Update and upgrade system:
```bash
sudo yay -Syyu
```
- Find file or folder (-d to find directory):
```bash
find <path-to-search> -type f -name "name"
```

- Cấp quyền cho thiết bị bên ngoài (các chip xử lý)
```bash
sudo chmod a+rw /dev/tty___
```
## Bluetooth connection:
- Check bluetooth status:
```bash
systemctl status bluetooth
```

- Start bluetooth daemon:
```bash
systemctl start bluetooth
```

- Make bluetooth run automatically when system starts:
```bash
systemctl enable bluetooth
```

## Fan Controller:
- Find and matching file configuration for laptop model:
```bash
nbfc config --recommend
nbfc config --set <MODEL>
```
- Start fan service:
```bash
nbfc start
```
- Check service status:
```bash
nbfc status -a 
```
- Automatically start on boot:
```bash
systemctl enable nbfc_service
```
- Adjust the fan speed:
```bash
nbfc set -s <percentage>
```

## Snapper:
- Config file path at: `/etc/snapper/configs/`
- Show config:
```bash
snapper list-configs
```
- List snapshot taken from a given configuration:
```bash
snapper -c <config> list
```
- Delete snapshots (if is root, replace config with root; delete multiple snap with space between):
```bash
snapper -c config delete <N>
```
- Create snapshot:
```bash
 snapper -c <config> create --description <desc>
```

## Debian:
- Install package:
```bash
dpkg -i <package-name.deb>
```
- List all package install by dpkg:
```bash
dpkg -l
```
- View a specific package:
```bash
dpkg -s <package-name>
```

## Firewall:
- Turn off the firewall:
```shell
ufw disable
```

## Link:
- Sym-link (soft-link):
```bash
ln -s <đường_dẫn_đích> <đường_dẫn_liên_kết>
```
- Shorten current directory:
```bash
PS1='\u:\W\$ '
```