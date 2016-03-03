
pkgname=slack
pkgver=2.0.0
pkgrel=1
pkgdesc="Slack Desktop (Beta) for Linux"
arch=('x86_64')
url="https://slack.com/apps"
license=('custom')
depends=('expat' 'gconf' 'gtk2' 'hunspell' 'hunspell-en' 'libgcrypt' 'libnotify' 'libxss' 'libxtst' 'xdg-utils')
optdepends=('libgnome-keyring')
source=("https://slack-ssb-updates.global.ssl.fastly.net/linux_releases/slack-desktop-${pkgver}-amd64.deb")
sha256sums=('9b39923c7e104c155a05ebd8ebdef287869da0deaf984ffc803e3399005c7340')


package() {
    bsdtar -O -xf "slack-desktop-${pkgver}"*.deb data.tar.xz | bsdtar -C "$pkgdir" -xJf -

    # Permission fix
    find "${pkgdir}" -type d -exec chmod 755 {} +

    # Remove all unnecessary stuff
    rm -rf "${pkgdir}/etc"
    rm -rf "${pkgdir}/usr/share/lintian"
    rm -rf "${pkgdir}/usr/share/doc"

    # Move license
    install -dm755 ${pkgdir}/usr/share/licenses/${pkgname}
    mv ${pkgdir}/usr/share/slack/LICENSE ${pkgdir}/usr/share/licenses/${pkgname}
    mv ${pkgdir}/usr/share/slack/LICENSES.chromium.html ${pkgdir}/usr/share/licenses/${pkgname}
    ln -s ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE ${pkgdir}/usr/share/slack/resources/LICENSE
}
