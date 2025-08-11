#Maintainer: Your Name email@example.com

pkgname=twitch-drops-miner-bin
pkgver=1.0.0 
pkgrel=1 
pkgdesc="Twitch Drops Miner packaged as an AppImage" 
arch=('x86_64' 'aarch64') 
url="https://github.com/DevilXD/TwitchDropsMiner" 
license=('custom')

if [[ $CARCH == "x86_64" ]]; 
  then source=("https://github.com/DevilXD/TwitchDropsMiner/releases/download/${pkgver}/Twitch.Drops.Miner.Linux.AppImage-x86_64") 
  sha256sums=('7d533bd3c1f886bde057153ddc44c01247e84b0faaa631747e089ad1eb038b6b') 
elif [[ $CARCH == "aarch64" ]]; 
  then source=("https://github.com/DevilXD/TwitchDropsMiner/releases/download/${pkgver}/Twitch.Drops.Miner.Linux.AppImage-aarch64") 
  sha256sums=('78d608b0d497e3a6dfd395857a2564df6f38bccab3e09cfe1903d3a7abf1ec3f') 
fi

package() { 
  install -Dm755 "${srcdir}/${source[0]##*/}" "${pkgdir}/usr/bin/twitch-drops-miner 
}