pkgbase=Brave
pkgname=brave
_pkgname=brave-bin
pkgver=1.49.132
_chromiumver=111.0.5563.147
pkgrel=1
pkgdesc='Web browser that blocks ads and trackers by default (binary release)'
arch=(x86_64)
url=https://brave.com/linux/#release-channel-installation
license=(MPL2 BSD custom:chromium)
depends=(alsa-lib
         gtk3
         libxss
         nss
         ttf-freefont
         ttf-ms-fonts)
optdepends=('cups: Printer support'
            'libnotify: Native notification support')
options=(!strip)
source=("https://github.com/brave/brave-browser/releases/download/v$pkgver/brave-browser-$pkgver-linux-amd64.zip"
        "$pkgname.sh"
        "brave-browser.desktop")
sha256sums=('SKIP'
            'SKIP'
            'SKIP')

prepare() {
	mkdir -p Brave
	bsdtar -xf "$pkgname-browser-$pkgver-linux-amd64.zip" -C Brave
	chmod +x Brave/brave
}

package() {
	install -dm0755 "$pkgdir/opt"
	cp -a Brave "$pkgdir/opt/$_pkgname"

	# allow firejail users to get the suid sandbox working
	chmod 4755 "$pkgdir/opt/$_pkgname/chrome-sandbox"

	install -Dm0755 "$pkgname.sh" "$pkgdir/usr/bin/brave"
	install -Dm0644 -t "$pkgdir/usr/share/applications/" "brave-browser.desktop"
	install -Dm0644 -t "$pkgdir/usr/share/licenses/$pkgname/" Brave/LICENSE
	pushd "$pkgdir/usr/"
	for size in 16x16 24x24 32x32 48x48 64x64 128x128 256x256; do
		install -Dm0644 "$pkgdir/opt/$_pkgname/product_logo_${size/x*/}.png" \
			"share/icons/hicolor/$size/apps/brave-desktop.png"
	done
}
