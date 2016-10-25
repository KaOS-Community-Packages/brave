pkgname=brave
pkgver=0.12.6
pkgrel=1
pkgdesc="A web browser automatically blocks ads and trackers"
arch=("x86_64")
url="https://www.brave.com/"
license=('GPL')
depends=('gconf' 'libcap' 'gtk2' 'nss' 'libxtst' 'libnotify' 'alsa-lib' 'libxss' 'libcups' 'libgnome-keyring' 'libxrandr')
source=("https://github.com/brave/browser-laptop/releases/download/v${pkgver}dev/brave_${pkgver}_amd64.deb")
md5sums=('bb22e7be188508579db86cadeae47409')
package() {
  tar -xJf $srcdir/data.tar.xz -C $pkgdir
  chmod -R 755 $pkgdir/usr
  rm -r $pkgdir/usr/share/{doc,lintian}
}
