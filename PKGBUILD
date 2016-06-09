pkgname=slack
pkgver=2.0.6
pkgrel=1
pkgdesc="Slack Desktop for Linux"
arch=('x86_64')
url="https://slack.com/apps"
license=('custom')
depends=( 'gconf' 'gtk2' 'hunspell' 'hunspell-en' 'libgcrypt' 'nss' 'libxtst' 'libnotify' 'xdg-utils' 'libxss' 'alsa-lib')
optdepends=('libgnome-keyring')
source=("https://slack-ssb-updates.global.ssl.fastly.net/linux_releases/slack-desktop-${pkgver}-amd64.deb")
sha256sums=('8c91ef57f4c4b2fec9e5d3d3ad6f54b7b15da269c041a0e1a37c76b133097528')

package() {
    bsdtar -xf data.tar.xz -C "${pkgdir}"
    find "${pkgdir}" -type d -exec chmod 755 {} +
    rm -rf "${pkgdir}/etc"
}
