pkgname=brave
pkgver=1.28.106
pkgrel=1
epoch=1
pkgdesc='Web browser that blocks ads and trackers by default (binary release)'
arch=(x86_64)
url=https://brave.com
license=(MPL2 BSD custom:chromium)
depends=(alsa-lib
         gtk3
         libxss
         nss
		 ttf-freefont
         ttf-ms-fonts)
optdepends=('cups: Printer support'
            'libgnome-keyring: Enable GNOME keyring support'
            'libnotify: Native notification support')
provides=("${pkgname%-bin}=$pkgver" 'brave-browser')
conflicts=("${pkgname%-bin}")
options=(!strip)
source=("$pkgname-$pkgver.zip::https://github.com/brave/brave-browser/releases/download/v$pkgver/brave-browser-$pkgver-linux-amd64.zip"
        "$pkgname.sh"
        'brave-browser.desktop')
noextract=("$pkgname-$pkgver.zip")
sha256sums=('dbed50ab91cd99ee15a84cb7977a395b2510e1dd2ee10ba437763fe72b180f23'
            'ba7d57a3328c68e6a78e49506af0e238936e823b2f463e8087c20fcf4300232a'
            'c07276b69c7304981525ecb022f92daf7ae125a4fb05ac3442157b50826e257a')

prepare() {
	mkdir -p brave
	bsdtar -xf "$pkgname-$pkgver.zip" -C brave
	chmod +x brave/brave
}

package() {
	install -dm0755 "$pkgdir/usr/lib"
	cp -a brave "$pkgdir/usr/lib/$pkgname"

	# allow firejail users to get the suid sandbox working
	chmod 4755 "$pkgdir/usr/lib/$pkgname/chrome-sandbox"

	install -Dm0755 "$pkgname.sh" "$pkgdir/usr/bin/brave"
	install -Dm0644 -t "$pkgdir/usr/share/applications/" "brave-browser.desktop"
	install -Dm0644 -t "$pkgdir/usr/share/licenses/$pkgname/" brave/LICENSE
	pushd "$pkgdir/usr/"
	for size in 16x16 24x24 32x32 48x48 64x64 128x128 256x256; do
		install -Dm0644 "lib/$pkgname/product_logo_${size/x*/}.png" \
			"share/icons/hicolor/$size/apps/brave-desktop.png"
	done
}
