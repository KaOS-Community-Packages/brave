pkgname=brave
_pkgname=brave-bin
pkgver=1.82.161
_chromiumver=140.0.7339.80
pkgrel=1
pkgdesc='Web browser that blocks ads and trackers by default (binary release)'
arch=('x86_64')
url='https://brave.com'
license=('MPL2 BSD custom:chromium')
depends=('alsa-lib' 'gtk3' 'libxss' 'nss' 'ttf-freefont' 'ttf-liberation' 'ttf-ms-fonts')
optdepends=('cups: Printer support'
            'libnotify: Native notification support')
options=(!strip)
source=("${pkgname}-${pkgver}.zip::https://github.com/brave/brave-browser/releases/download/v${pkgver}/brave-browser-${pkgver}-linux-amd64.zip"
        "${pkgname}.sh"
        "brave-browser.desktop")
sha256sums=('SKIP'
            'SKIP'
            'SKIP')

prepare() {
	bsdtar -xf "${pkgname}-${pkgver}.zip"
	chmod +x ${srcdir}
}

package() {
	msg "Prepare dirs and copy files"
	install -dm0755 "${pkgdir}/opt"
	cp -a ${srcdir} "${pkgdir}/opt/${pkgname}"

	install -Dm0755 "${pkgname}.sh" "${pkgdir}/usr/bin/brave"
	install -Dm0644 -t "${pkgdir}/usr/share/applications/" "brave-browser.desktop"
	install -Dm0644 -t "${pkgdir}/usr/share/licenses/${pkgname}/" ${srcdir}/LICENSE
	pushd "${pkgdir}/usr/"

	msg "Copy icons"
	for size in 16x16 24x24 32x32 48x48 64x64 128x128 256x256; do
		install -Dm0644 "${pkgdir}/opt/${pkgname}/product_logo_${size/x*/}.png" \
			"share/icons/hicolor/${size}/apps/brave-desktop.png"
	done

	msg "Correct rights"
	# allow firejail users to get the suid sandbox working
	chmod 4755 "${pkgdir}/opt/${pkgname}/chrome-sandbox"
}
