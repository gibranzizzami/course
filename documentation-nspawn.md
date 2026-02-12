##### directory containers
```
mkdir mycontainers
```
#### packages
```
sudo pacman -S arch-install-scripts 
```
```
sudo pacstrap -K -c mycontainers base 
```
#### set root password
```
sudo systemd-nspawn -D mycontainers
```
```
passwd
```
```
logout
```
#### booting the container
```
sudo systemd-nspawn -b -D mycontainers
```


### systemd-nspawn-tutorial for ubuntu
#### install debootstrap
```
pacman -S debootstrap (for arch linux's user)
```
#### make new directory containers
```
mkdir containers
```
#### get full functionality in systemd-based systems
```
debootstrap --include=dbus,libpam-systemd stable containers
```
#### set root password
```
systemd-nspawn -D containers
```
```
passwd
```
```
logout
```
####  booting the containers
```
systemd-nspawn -b -D containers
```


### systemd-nspawn for alma linux
#### install dnf
```
pacman -S dnf
```
#### make a new file
```
/etc/dnf/dnf.conf
```
#### fill the /etc/dnf/dnf.conf
```
[baseos]
name=AlmaLinux $releasever - BaseOS
mirrorlist=https://mirrors.almalinux.org/mirrorlist/$releasever/baseos
gpgkey=https://repo.almalinux.org/almalinux/RPM-GPG-KEY-AlmaLinux-$releasever
```
#### make a directory
```
mkdir /var/lib/machines/alma-container
```
#### install alma linux 9
```
dnf --repo=baseos --releasever=9 --best --installroot=/var/lib/machines/alma-container --setopt=install_weak_deps=False install almalinux-release dhcp-client dnf glibc-langpack-en iproute iputils less passwd systemd vim-minimal
```
#### set root password
```
systemd-nspawn -D /var/lib/machines/alma-container passwd
```
### booting the containers
```
systemd-nspawn -b -D /var/lib/machines/alma-container
```
