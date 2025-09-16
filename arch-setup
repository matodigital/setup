#!/usr/bin/env bash
set -euo pipefail

RED='\033[0;31m'
YELLOW='\033[1;33m'
GREEN='\033[0;32m'
BLUE='\033[0;34m'
NC='\033[0m'

trap 'echo -e "${RED}[✗] Script failed at line $LINENO${NC}" >&2' ERR

PKGS=(
        xorg-server
        xorg-xinit
        xorg-xinput
        xorg-setxkbmap
        xterm
        # xcolor

        gnu-free-fonts

        # dunst
        maim
        xwallpaper
        # ? (swayidle)
        slock
        xorg-xev
        xclip
        screenkey
        xdotool

        7zip
        asciinema
        asciiquarium
        astroterm
        atac
        bc
        blueman
        bluez # already installed by blueman
        bluez-utils
        bridge-utils
        brightnessctl
        btop
        calcurse
        chafa
        chromium
        clang
        cmake
        cups
        cups-pdf
        dbeaver
        dmidecode
        dnsmasq
        docker
        emacs
        fastfetch
        ffmpeg
        figlet
        firefox
        font-manager
        fq
        freerdp
        fzf
        gammastep
        gdb
        gedit
        ghostty
        gimp
        # git
        gitu
        glow
        go-yq
        htop
        imagemagick
        imv
        jc
        jdk-openjdk
        jdk21-openjdk
        jq
        k9s
        kolourpaint
        lazydocker
        lazygit
        less
        libzip # needed for php and composer via mise
        man-db
        mariadb
        minikube
        mise
        mpv
        ncdu
        neovim
        newsboat
        noto-fonts-cjk
        noto-fonts-emoji
        obs-studio
        obsidian
        pass
        pastel
        pavucontrol
        playerctl
        podman
        # polkit
        poppler
        postgresql
        qemu-base
        qt5ct
        qt6ct
        qutebrowser
        re2c # needed for php and composer via mise
        remmina
        ripgrep
        rsync
        snes9x-gtk
        solaar
        # sqlite
        stow
        system-config-printer
        task
        thunar
        tmux
        tree
        ttf-nerd-fonts-symbols
        udiskie
        udisks2 # already installed by udiskie
        unrar
        unzip
        usbutils
        # vifm
        virt-manager
        webkit2gtk-4.1 # needed for tauri apps
        wezterm
        xdg-desktop-portal
        xdg-desktop-portal-gtk
        yazi
        yt-dlp
        zathura
        zathura-cb
        zathura-pdf-mupdf
        zathura-ps
        zed
        zip
)

AUR_PKGS=(
        android-studio
        bemoji
        cbonsai
        cursor-bin
        google-chrome
        lavat-git
        lazysql
        localsend-bin
        python-terminaltexteffects
        timr
        trmt
        # xfce-polkit
)

echo -e "${BLUE}[*] Updating system...${NC}"
sudo pacman -Syu --noconfirm

echo -e "${BLUE}[*] Installing official repo packages...${NC}"
sudo pacman -S --needed "${PKGS[@]}"
echo -e "${GREEN}[✓] Official repo packages installed!${NC}"

echo -e "${BLUE}[*] Installing PARU...${NC}"
tmpdir=$(mktemp -d)
cd "$tmpdir"
git clone https://aur.archlinux.org/paru.git
cd paru
echo -e "${YELLOW}[!] Building PARU...${NC}"
makepkg -sirc --noconfirm
cd /
rm -rf "$tmpdir"
echo -e "${GREEN}[✓] PARU installed!${NC}"

echo -e "${BLUE}[*] Installing AUR packages...${NC}"
paru -S --needed "${AUR_PKGS[@]}"
echo -e "${GREEN}[✓] AUR packages installed!${NC}"

echo -e "${GREEN}[✓] All installations completed successfully!${NC}"
