1. Sambungin wifi
```
iwctl station wlan0 connect [ssid]
```

2. format boot
```
mkfs.vfat -F32 -n BOOT /dev/[partisi boot]
```

3. mounting boot
```
mkdir /mnt/boot
```

```
mount -o uid=0,gid-0,fmask=0077,dmask=0077 /dev/[partisi boot] /mnt/boot
```

4. Format root
```
mkfs.ext4 -b 4096 /dev/[partisi root]
```

5. Mounting root
```
mount /dev/[partisi root] /mnt
```

6. Format data
```
mkfs.ext4 -b 4096 /dev/[partisi data]
```

7. Buat direktori /mnt/home
```
mkdir /mnt/home
```

8. Mounting home
```
mount /dev/[partisi home] /mnt/home
```

9. Cek perangkat 
```
lspci
```
Nanti ingetin merek apa aja yang ada di perangkat setelah itu tambahin di step selanjutnyakalau mislanya ada merek yang beda

10. Install package
Sesuaikan dengan perangkat laptop 
```
pacstrap /mnt linux linux-headers mkinitcpio intel-ucode linux-firmware-intel  base base-devel git neovim iwd firewalld iptables-nft aria2 fuse bash-completion impala wget
```

11. Regist partisi
```
genfstab -U /mnt > /mnt/etc/fstab
```
Untuk cek berhasil atau tidak gunakan command
```
cat /mnt/etc/fstab
```
Jika parrisi boot root dan home ada berarti berhasil

12.  Copy network config
```
cp /etc/systemd/network/* /mnt/etc/systemd/network
```

```
mkdir /mnt/var/lib/iwd
```

```
cp -r /var/lib/iwd /mnt/var/lib/iwd
```

12. Masuk ke root
```
arch-chroot /mnt
```

13.  Install tampilan
```
pacman -S hyprland hyprlock xdg-desktop -portal-hyprland hyprpolkitagent hypridle hyprshot gnome-keyring libsecret superfile perl-image-exiftool lite-xl libnewt uwsm waybar mako wofi brightnessctl cliphist wl-clipboard mpd mpc mpv yt-dlp kitty qt5-wayland qt6-wayland bluez blueman firefox-developer-edition pipewire pipewire-pulse pipewire-jack pipewire-alsa wireplumber pamixer ttf-jetbrains-mono-nerd ttf-droid ttf-roboto ttf-fira-sans ttf-opensans btop rocm-smi-lib
```

14. Buat hostname
```
echo nama_hostname > etc/hostname
```

15. Time 
```
ln -sf /usr/share/zoneinfo/Asia/Jakarta /etc/localtime
```

```
hwclock --systohc
```

```
nvim /etc/locale.gen
```

Cari en_US
Terus uncommadting

```
locale-gen
```

```
locale > /etc/locale.conf
```

```
nvim /etc/locale.conf
```

samakan isinya seperti di bawah ini
```
LANG=en_US.UTF-8
LC_CTYPE="C.UTF-8"
LC_NUMERIC="C.UTF-8"
LC_TIME="C.UTF-8"
LC_COLLATE="C.UTF-8"
LC_MONETARY="C.UTF-8"
LC_MESSAGES=
LC_PAPER="C.UTF-8"
LC_NAME="C.UTF-8"
LC_ADDRESS="C.UTF-8"
LC_TELEPHONE="C.UTF-8"
LC_MEASUREMENT="C.UTF-8"
LC_IDENTIFICATION="C.UTF-8"
LC_ALL=
```

16. User
```
useradd -m 'nama_user'
```

```
passwd 'nama_user'
```

```
usermod -aG wheel 'nama_user'
```

17.  Uncomenting
```
nvim /etc/sudoers
```

uncomenting [%wheel ALL=(ALL:ALL) ALL]

18. Cmdline
```
mkdir /etc/cmdline.d
```

```
touch /etc/cmdline.d/{01-boot.conf,02-mods.conf,03-secs.conf,04-perf.conf,05-nets.conf,06-misc.conf}
```

```
nvim /etc/cmdline.d/01-boot.conf
```
Di dalam nya tambahin 
```
root=/dev/'partisi rootnya'
```


```
nvim /etc/cmdline.d/06-misc.conf
```
Tambahkan
```
rw quiet
```

Lanjut
```
cd /etc
```

```
ls
```

Hapus mkinitcpio.conf.d jika ada

```
rm -fr mkinitcpip.conf.d
```

Pindahkan
```
mv /etc/mkinitcpio.conf /etc/mkinitcpio.d/default.conf
```

Lanjut
```
cd mkinitcpio.d
```

```
ls
```

```
nvim linux.preset
```
samakan isinya dengan dibawah ini
```
# mkinitcpio preset file for the 'linux-zen' package

ALL_config="/etc/mkinitcpio.d/default.conf"
ALL_kver="/boot/kernel/vmlinuz-linux-zen"
ALL_kerneldest="/boot/kernel/vmlinuz-linux-zen"

PRESETS=('default')
#PRESETS=('default' 'fallback')

#default_config="/etc/mkinitcpio.conf"
#default_image="/boot/initramfs-linux-zen.img"
default_uki="/boot/efi/linux/arch-linux-zen.efi"
#default_options="--splash /usr/share/systemd/bootctl/splash-arch.bmp"

#fallback_config="/etc/mkinitcpio.conf"
#fallback_image="/boot/initramfs-linux-zen-fallback.img"
#fallback_uki="/efi/EFI/Linux/arch-linux-zen-fallback.efi"
#fallback_options="-S autodetect"
```
note: seusaikan dengan kernel kalian

```
cd /boot
```

```
mkdir kernel efi
```

```
mv intel-* atau amd-* kernel
```

```
mv vmlinuz-* kernel
```

```
rm -fr initramfs-*
```

```
bootctl --path=/boot install
```

```
mkinitcpio -P
```

```
exit
```

```
umount -R /mnt
```

```
reboot
```

After booting

```
sudo systemctl enable --global waybar
```

```
sudo systemctl enable --global hypridle
```

```
sudo systemctl enable --global hyprpolkitagent
```

```
sudo systemctl enable systemd-networkd
```

```
sudo systemctl enable systemd-resolved
```

```
sudo systemctl enable iwd
```

```
sudo systemctl start iwd
```

config hyprland
```
git clone https://github.com/almuhdilkarim/galium
```

```
cd galium
```

```
chmod +x install
```

```
./install
```
