pkgname=brave
pkgver=0.17.16
pkgrel=1
pkgdesc="A web browser automatically blocks ads and trackers"
arch=("x86_64")
url="https://www.brave.com/"
license=('GPL')
depends=('gcc-libs' 'gtk3' 'nss' 'gconf' 'libjpeg-turbo' 'freetype2' 'cairo' 'libxslt' 'libpng' 'alsa-lib' 'libxss' 'hicolor-icon-theme' 'xdg-utils' 'chromium-ffmpeg-codecs' 'widevine')
source=("https://github.com/brave/browser-laptop/releases/download/v${pkgver}dev/brave_${pkgver}_amd64.deb")
md5sums=('e407e3b202e6b9a7bcd4a206630b658a')
package() {
  tar -xJf $srcdir/data.tar.xz -C $pkgdir
  chmod -R 755 $pkgdir/usr
  rm -r $pkgdir/usr/share/{doc,lintian}
}
