# Maintainer: PandaDEV <contact@pandadev.net>
pkgname=twitch-drops-miner-bin
pkgver=16.0
pkgrel=1
pkgdesc="An app that allows you to AFK mine timed Twitch drops, with automatic drop claiming and channel switching. "
arch=(x86_64 aarch64)
url="https://github.com/DevilXD/TwitchDropsMiner"
license=('MIT')
options=('!strip')
depends=()
provides=(twitch-drops-miner)
conflicts=(twitch-drops-miner)
source_x86_64=("Twitch.Drops.Miner-x86_64.AppImage::https://github.com/DevilXD/TwitchDropsMiner/actions/runs/16847076869/artifacts/3725324177")
source_aarch64=("Twitch.Drops.Miner-aarch64.AppImage::https://assets.dataflare.app/release/linux/aarch64/Dataflare.AppImage")
sha256sums_x86_64=('ec6affea27ca19a696b017647743a66be55306c6e3a206e679f7054122fe6709')
sha256sums_aarch64=('2b03cb8ae4588e5ca2a141ee50ae9259db79a5ae9a8322ae13ad18aae8febcf1')

package() {
    install -Dm755 *.AppImage "$pkgdir/opt/twitch-drops-miner/twitch-drops-miner.appimage"
    
    install -dm755 "$pkgdir/usr/bin"
	cat > "$pkgdir/usr/bin/twitch-drops-miner" << 'EOF'
#!/bin/bash
export APPIMAGE_EXTRACT_AND_RUN=1
exec /opt/twitch-drops-miner/twitch-drops-miner.appimage "$@"
EOF
    chmod +x "$pkgdir/usr/bin/twitch-drops-miner"
    
    chmod +x *.AppImage
    ./*.AppImage --appimage-extract >/dev/null 2>&1
    
    if [ -f squashfs-root/*.desktop ]; then
        install -dm755 "$pkgdir/usr/share/applications"
        desktop_file=$(find squashfs-root -name "*.desktop" -type f | head -1)
        sed 's|Exec=.*|Exec=twitch-drops-miner %U|g' "$desktop_file" > "$pkgdir/usr/share/applications/twitch-drops-miner.desktop"
    fi
    
    png_file=$(find squashfs-root -name "*.png" -type f | head -1)
    if [ -n "$png_file" ]; then
        install -Dm644 "$png_file" "$pkgdir/usr/share/pixmaps/twitch-drops-miner.png"
    fi
    
    rm -rf squashfs-root
}
