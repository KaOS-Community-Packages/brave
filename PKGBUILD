pkgname=brave
pkgver=0.9.2
pkgrel=2
pkgdesc="A web browser automatically blocks ads and trackers"
arch=("x86_64")
url="https://www.brave.com/"
license=('GPL')
depends=('gconf' 'libcap' 'gtk2' 'nss' 'libxtst' 'libnotify' 'alsa-lib' 'libxss' 'libcups' 'libgnome-keyring' 'libxrandr')
source=("https://github.com/brave/browser-laptop/releases/download/v${pkgver}dev/brave_${pkgver}_amd64.deb")
md5sums=('a4b25b1111af31f77619bfa28dea9d0e')

package() {
  tar -xJf $srcdir/data.tar.xz -C $pkgdir
  chmod -R 755 $pkgdir/usr
  rm -r $pkgdir/usr/share/{doc,lintian}
}
