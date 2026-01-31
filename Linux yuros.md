1. Sambungin wifi
2. Format root
```
mkfs.ext4 -b 4096 /dev/[path]
```

3. Mounting root
```
mount /Dev/[path] /mnt
```

4. Buat direktori /mnt/boot
```
mkdir /mnt/boot
```

5. Format boot
```
mount -o uid=0,gid=0,fmask=0077,dmask=0077 /dev/[path] /mnt
```

6. Format data
```
mkfs.ext4 -b 4096 /dev/[path]
```

7. Buat direktori /mnt/home
```
mkdir /mnt/home
```

8. Mounting home
```
mount /Dev/[path] /mnt/home
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
Cat /mnt/etc/fstab
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
![[20260130_172312.jpg]]

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
![[IMG-20260123-WA0001.jpg]]

```
cd /boot
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