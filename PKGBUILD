pkgname=slack
pkgver=2.0.1
pkgrel=1
pkgdesc="Slack Desktop for Linux"
arch=('x86_64')
url="https://slack.com/apps"
license=('custom')
depends=( 'gconf' 'gtk2' 'hunspell' 'hunspell-en' 'libgcrypt' 'nss' 'libxtst' 'libnotify' 'xdg-utils' 'libxss' 'alsa-lib')
optdepends=('libgnome-keyring')
source=("https://slack-ssb-updates.global.ssl.fastly.net/linux_releases/slack-desktop-${pkgver}-amd64.deb")
sha256sums=('12d84e61ba366cc5bac105b3f9930f2dfdd64c1e5fabbb08a6877e1c98bfb9c7')

package() {
    bsdtar -xf data.tar.xz -C "${pkgdir}"
    find "${pkgdir}" -type d -exec chmod 755 {} +
    rm -rf "${pkgdir}/etc"
    ln -s ${pkgdir}/usr/share/${pkgname}/LICENSE ${pkgdir}/usr/share/slack/resources/LICENSE
}
