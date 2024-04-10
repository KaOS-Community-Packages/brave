pkgname=brave
_pkgname=brave-bin
pkgver=1.64.113
_chromiumver=123.0.6312.86
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
sha256sums=('cea5bf71864d2d781f45ec6df24f125768f878cfc068d72243d18616feb60ca5'
            '18e149cb7e76d8ffea63793e4471e7233bda8345ebf14896fdd1e07385cdac32'
            'c07276b69c7304981525ecb022f92daf7ae125a4fb05ac3442157b50826e257a')

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
