pkgname=brave
_pkgname=brave-browser
pkgver=1.64.116
pkgrel=1
pkgdesc='Web browser that blocks ads and trackers by default (binary release)'
arch=('x86_64')
url='https://brave.com'
license=('MPL2' 'BSD' 'custom:chromium')
depends=('alsa-lib' 'gtk3' 'libxss' 'nss' 'ttf-freefont' 'ttf-liberation')
optdepends=('cups: Printer support'
			'sane: Scanner support'
			'libnotify: Native notification support')
options=('!strip')
source=("${_pkgname}-${pkgver}-linux-amd64.zip::https://github.com/brave/brave-browser/releases/download/v${pkgver}/${_pkgname}-${pkgver}-linux-amd64.zip"
		"${pkgname}.desktop" )
sha256sums=('SKIP' 'SKIP')

package() {
	msg2 "Unpacking SOURCE files of the downloaded ZIP binary archive"
	mkdir -p "${pkgdir}/opt/Brave/"
	bsdtar -xf "${srcdir}/${_pkgname}-${pkgver}-linux-amd64.zip" -C "${pkgdir}/opt/Brave/"

	msg2 "Removing unnecessary file properties from the DEB binary package"
	rm -fdrv "${pkgdir}/opt/Brave/cron/"

	chmod 0755 "${pkgdir}/opt/Brave/"
	# Allow FireJail users to get the SUID sandbox working
	msg2 "Impose sandboxing by modifying SUID properties"
	chmod 4755 -v "${pkgdir}/opt/Brave/chrome-sandbox"

	msg2 "Installing and linking files from SOURCE to the system"
	install -Dm0644 "${srcdir}/${pkgname}.desktop" -t "${pkgdir}/usr/share/applications/"
	install -Dm0644 "${pkgdir}/opt/Brave/LICENSE" -t "${pkgdir}/usr/share/licenses/${pkgname}/"
	install -Dm0644 "${pkgdir}/opt/Brave/product_logo_256.png" "${pkgdir}/usr/share/pixmaps/${pkgname}.png"

	install -d "${pkgdir}/usr/share/icons/hicolor/256x256/apps/"
	ln -sv "/opt/Brave/product_logo_256.png" "${pkgdir}/usr/share/icons/hicolor/256x256/apps/${pkgname}.png"

	install -d "${pkgdir}/usr/bin/"
	ln -sv "/opt/Brave/brave" -t "${pkgdir}/usr/bin/"

	msg2 "DONE"
}
