pkgname=slack
pkgver=2.8.2
pkgrel=1
pkgdesc="Slack Desktop for Linux"
arch=('x86_64')
url="https://slack.com/apps"
license=('custom')
depends=('gconf' 'gtk2' 'expat' 'hunspell' 'libgcrypt' 'nss' 'libxtst' 'libnotify' 'xdg-utils' 'libxss' 'alsa-lib' 'libgnome-keyring')
source=("https://slack-ssb-updates.global.ssl.fastly.net/linux_releases/slack-desktop-${pkgver}-amd64.deb"
        "${pkgname}.desktop")
md5sums=('1132730a0c3493d72049c7123507642b'
         '479d61dd5f731b3c5d67dba2e5aec2d6')

package() {
    bsdtar -xf data.tar.xz

    mkdir -p ${pkgdir}/opt/${pkgname} ${pkgdir}/usr/bin
    cp -R usr/lib/${pkgname}/* ${pkgdir}/opt/${pkgname}
    install -Dm644 ${pkgname}.desktop ${pkgdir}/usr/share/applications/${pkgname}.desktop
    install -Dm644 usr/share/pixmaps/${pkgname}.png ${pkgdir}/usr/share/icons/hicolor/512x512/apps/${pkgname}.png
    ln -s /opt/${pkgname}/${pkgname} ${pkgdir}/usr/bin/${pkgname}
}
